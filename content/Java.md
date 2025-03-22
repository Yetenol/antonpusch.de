---
date: "2025-03-22T23:21:56.791+01:00"
title: "Java"
description: "A platform independent, object-oriented programming framework designed to be simple, secure, and robust"
dg-publish: true
---

# Datentypen

## Typecasting

- byte ➜ short ➜ int ➜ long
- float ➜ double

# Functions

## Parameter Passing

- stored in **stack memory**
- `Primitive variable:` stores its actual values
- `Non-primitive variables:` stores the reference variable which point to the address of the object they're referring to
  - During invocation:
- Arguments are always passed-by-value

### Method invocation

- `Primitive variable:`
  - copy value inside stack memory
  - pass **value** to the callee method
- `Non-primitive variables:`
  - a reference in stack memory points to the actual data which resides in the heap
- `Objects:`
  - copy the reference from stack memory
  - pass **reference** to callee method

# Klassen

```java
public class <Name> {
    // Attribute
    // Konstruktor
    // Methoden
}
```

## Konstructor

```java
public <Klassenname>(<Parameter>) {
<Initialisierung>
}
```

## Statische Methoden

```java
public static void main(String[] args)
```

- wird benötigt, wenn die Methode auch ohne erstellen eines Objektes aufrufbar sein soll

## Datenübergabe

- primitive Datentypen werden als _passed-by-value_ übergeben
- complexe Datentypen und strukturierte Objekte werden als _passed-by-reference_

# Objekte

```java
Modul algodat = new Modul( );
```

### Objekte kopieren

```java
Modul algodat = new Modul( );
Modul introprog = algodat;
```

- nur ein Objekt wurde erzeugt

Sources:
- 2022-05-04: [Pass-By-Value as a Parameter Passing Mechanism in Java - Baeldung](https://www.baeldung.com/java-pass-by-value-or-pass-by-reference)
