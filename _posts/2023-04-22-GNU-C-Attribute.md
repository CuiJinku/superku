---
layout: post
title: "Learning GNU C __attribute__"
date: 2023-04-22
---

## What is `__attribute__`?


The `__attribute__` mechanism can decorate variables, assign characteristic to declared functions, and etc. It is a mechanism to allow programmers interact with compilers. Programmiers can utilize attribute mechanism to explicitly tell compilers some behaviros are intentional, such as
 * Do not report them as neither warnings, erros, or undefined behavirors. 
 * Do not optimize them. 
 * ...

I believe if Rust language has this mechanism, some programmers would like tell Rust compilers:

> **Do NOT panic on my code !!!**.


The following content are based on that essay: [Using GNU C \_\_attribute\_\_](http://unixwiz.net/techtips/gnu-c-attributes.html)

### \_\_attribute\_\_ unused




