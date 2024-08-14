---
dg-publish: true
---

> If you need more than 3 levels of indentation, you're screwed anyway and should fix your program.
> -- [Linus Torvalds](https://libquotes.com/linus-torvalds/quote/lbq4a8n) in Linux 1.3.53 CodingStyle documentation (1995). Retrieved on 2011-08-13. - 1995-99

- constraining how much you nest, forces you to write better code
- deeply nested code often violates of single responsibility principle

# Extract into its own function

Extract inner parts of loop, conditions or if statements into its own function

```
Function calculate something
    Loop over field
        If element is even
            Modify element
        Endif
    Endloop
Endfunction
```

```
Function filter even numbers
    If element is even
        Modify element
    Endif
Endfunction

Function calculate something
    Loop over field
        Call filter even numbers
    Endloop
Endfunction
```

# Invert happy and unhappy paths

Rearrange your conditions and put your happy path at the end of functions

```
Function calculate something
    If parameter invalid
        Throw error 😡
    Else
        If another unhappy condition
            Return nothing 😡
        Else
            Happy path 🙂
        Endif
    Endif
Endfunction
```
- Happy path is **hard to identify** and deeply nested

```
Function 
    If parameter invalid
        Throw error 😡
    Endif
    
    If another unhappy condition
        Return nothing 😡
    Endif
    
    Happy path 🙂
Endfunction
```
- Deal with **unhappy** or exceptional path cases **first**
- Identify unhappy paths using **early exists** or **short circuits**
- Error paths are indented and can be **mentally discarded**
- Start your function with a **flat list of conditionals**
- Happy path moves down the function


Avoid nesting the happy pay in many conditions

# Inspiration
| Video                                                                                                                                                                                                                                                                            | Information                                                                                                                                                                                                                                                                                           |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <div class="video dataview-table"><iframe src="https://www.youtube-nocookie.com/embed/CFRhGnuXG-4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div> | [Why You Shouldn't Nest Your Code](https://www.youtube.com/watch?v=CFRhGnuXG-4) <br> from [CodeAesthetic](http://www.youtube.com/@CodeAesthetic) <br> on 2022-00-06 <br> about Education <br> taking 8 minutes, 29 seconds <br> see [Automatic captions](./Why%20You%20Shouldnt%20Nest%20Your%20Code.md) |


---
Sources:
- 2023-03-22: [Why You Shouldnt Nest Your Code](./Why%20You%20Shouldnt%20Nest%20Your%20Code.md)
- 2023-03-22: [Why you should reduce nesting blocks in your code, with practical refactoring tips | by Brook Novak | Medium](https://medium.com/@brooknovak/why-you-should-reduce-nesting-blocks-in-your-code-with-practical-refactoring-tips-11c122735559)
- 2023-03-22: [Replace Nested Conditional with Guard Clauses](https://refactoring.guru/replace-nested-conditional-with-guard-clauses)

Related:

Tags:
[Code aesthetics and refactoring](./Code%20aesthetics%20and%20refactoring.md)