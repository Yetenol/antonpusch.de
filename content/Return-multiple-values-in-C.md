---
date: "2025-07-17T08:13:58.704+02:00"
title: "Return multiple values in C"
description: "-"
dg-publish: true
---

# Option 1: Validating property

Return a structure `struct Bundle`. If its property `is_valid` is false, discard the rest of the structure's data.
- [p] Looks very similar to a function with a single return value.
- [p] Very readable, what the function returns
- [p] Multiple invalid states can be implemented.
- [p] Addition data can to attached to an invalid bundle.
- [p] Bundle can be stored as pointer and as local variable.
- [c] Without a validation check, an invalid bundle looks similar to a valid one.
```c
#include <stdlib.h>
#include <stdio.h>
#include <stdbool.h>

struct Bundle {
    _Bool is_valid;
    int triple, square;
};

struct Bundle get_bundle(int number) {
    struct Bundle bundle = {0};
    if (number < 2) {
        bundle.is_valid = false;
        return bundle;
    }

    bundle = (struct Bundle) {
        .is_valid = true,
        .triple = number * 3,
        .square = number * number
    };
    // bundle.triple = number * 3;
    return bundle;
}

int main(int argc, char *argv[]) {
    struct Bundle bundle;

    bundle = get_bundle(argc);
    if (bundle.is_valid == false) {
        perror("Too few arguments\n");
        exit(EXIT_FAILURE);
    }

    printf("Bundled are the multiples %i and %i\n", bundle.triple, bundle.square);
}
```

# Option 2: Optional pointer

Return the reference to a new dynamically (on the heap) allocated structure `struct Bundle *`. If the pointer is `NULL`, no bundle was created.
- [p] Accessing properties of an invalid bundle throws an error, thus requiring a validation check.
- [c] The return value must be released later as long as it is valid.
- [c] The bundle must be saved and used as a pointer `bundle->property`
```c
#include <stdlib.h>
#include <stdio.h>

#define INVALID_BUNDLE NULL
struct Bundle {
    int triple, square;
};

struct Bundle *new_bundle(int number) {
    struct Bundle *bundle = malloc(sizeof(struct Bundle));
    *bundle = (struct Bundle) {0};

    if (number < 2) {
        return INVALID_BUNDLE;
    }

    *bundle = (struct Bundle) {
        .triple = number * 3,
        .square = number * number
    };
    // bundle->triple = number * 3;
    return bundle;
}

int main(int argc, char *argv[]) {
    struct Bundle *bundle;

    bundle = new_bundle(argc);
    if (bundle == INVALID_BUNDLE) {
        perror("Too few arguments\n");
        exit(EXIT_FAILURE);
    }

    printf("Bundled are the multiples %i and %i\n", bundle->triple, bundle->square);
    if (bundle != NULL) {
        free(bundle);
    }
}
```

# Option 3: Output parameter

Save to the bundle given as a parameter. If false is returned, discard the bundle.
- [p] Behavior used by the standard library
- [p] Multiple invalid states can be implemented.
- [p] Return value does not have to be saved. 
- [p] Bundle can be stored as pointer and as local variable.
- [c] Hard to read what the function actually does.
- [c] Hard to read which parameters are for input and which for output.
- [c] Hard to read whether and where bundle gets initialized/modified.
```c
#include <stdlib.h>
#include <stdio.h>
#include <stdbool.h>

struct Bundle {
    int triple, square;
};

_Bool did_store_bundle(int number, struct Bundle *bundle_output) {
    *bundle_output = (struct Bundle) {0};

    if (number < 2) {
        return false;
    }

    *bundle_output = (struct Bundle) {
            .triple = number * 3,
            .square = number * number
    };
    // bundle_output->triple = number * 3;
    return true;
}

int main(int argc, char *argv[]) {
    struct Bundle bundle;

    if (did_store_bundle(argc, &bundle) == false) {
        perror("Too few arguments\n");
        exit(EXIT_FAILURE);
    }

    printf("Bundled are the multiples %i and %i\n", bundle.triple, bundle.square);
}
```

```c
#include <stdlib.h>
#include <stdio.h>

struct Bundle {
    int triple, square;
};

enum Status_store_bundle {
    TOO_FEW_ARGUMENTS,
    SMALL,
    LARGE
};

enum Status_store_bundle did_store_bundle(int number, struct Bundle *bundle_output) {
    *bundle_output = (struct Bundle) {0};

    if (number < 2) {
        return TO_FEW_ARGUMENTS;
    }

    *bundle_output = (struct Bundle) {
            .triple = number * 3,
            .square = number * number
    };
    // bundle_output->triple = number * 3;
    if (number < 3) {
        return SMALL;
    }
    return LARGE;
}

int main(int argc, char *argv[]) {
    struct Bundle bundle;

    switch (did_store_bundle(argc, &bundle)) {
        default:
        case TOO_FEW_ARGUMENTS:
            perror("Too few arguments\n");
            exit(EXIT_FAILURE);
            break;
        case SMALL:
            printf("Few arguments\n");
            break;
        case LARGE:
            printf("Many arguments\n");
            break;
    };

    printf("Bundled are the multiples %i and %i\n", bundle.triple, bundle.square);
}
```

---
Sources:

Related:

Tags:
[Blog](Blog.md)
[C Programming Language](C%20Programming%20Language.md)
[Discussions](./Discussions.md)
Software Development
