---
title: "Comments - Express way of intent with code not comments"
dg-publish: true
---

- comment **why** you're doing something, not **what**
- code is a much better **way of intent** than comments about code
- if you feel like you need human language to describe your code, see if you can make your code more human

![Pasted image 20230118151520.png](./attachments/pasted%20image%2020230118151520.png)

# Code Documentation

- describes high level architecture and public api of the system
- how code is **used**
- document what a class or API **represents**
- document interface **expectations**
    - Thread safety
    - Possible states
    - Error conditions
    - helps consumers how to use it
    - helps new implementers how it operates 

# Code Comments 

- describes how the code works
- how code **works**
- comment non obvious performance optimizations and why the code looks weird 
- comment references to sources of math or algorithms 
- comments can **lie**, code cannot
- tests, compiler checks, linting reduce bugs in code, comments are not checked 

## Code get bugs 

- if you change the code, comments easily get outdated
- comments aren't validate like code with tests, compiler checks, linting

# Improve code quality

- name variables to describe parts of the expression
- refactor the expression so it reads like the comment does
- if you describe what your code does, replace the code with a one-liner function named **what** it does
- extract **complex conditions** into it's own function
- **strongly type** to indicate content and ownership
 - code is just a more precise way of writing a spec

![Pasted image 20230118145631.png](./attachments/pasted%20image%2020230118145631.png)

| Video                                                                                                                                                                                                                                                                            | Information                                                                                                                                                                                                                                                           |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <div class="video dataview-table"><iframe src="https://www.youtube-nocookie.com/embed/Bf7vDBBOBUA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div> | [Don't Write Comments](https://www.youtube.com/watch?v=Bf7vDBBOBUA) <br> from [CodeAesthetic](http://www.youtube.com/@CodeAesthetic) <br> on 2023-00-16 <br> about Education <br> taking 5 minutes, 55 seconds <br> see [Transcript](./dont%20write%20comments.md) |


---
Sources:
- 2023-01-18: [Why You Shouldn't Nest Your Code](https://www.youtube.com/watch?v=CFRhGnuXG-4)
- 2023-01-18: [Naming Things in Code](https://www.youtube.com/watch?v=-J3wNP6u5YU)
- 2023-01-18: [Dont Write Comments](./dont%20write%20comments.md)

Related:
[Software Design Philosophy](Software%20Design%20Philosophy.md)
[Code aesthetics and refactoring](./code%20aesthetics%20and%20refactoring.md)

Tags:
[Discussions](./discussions.md)
