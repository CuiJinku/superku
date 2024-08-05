---
layout: post
title: "The Rust Programming Language"
date: 2024-07-24
---

## Foreword

## Introduction

## 1. Getting Started


### 1.1 Installation

```shell
rustc --version
rustup update
rustup self uninstall
rustup doc
```

### 1.2 Hello, World!
```shell
rustc main.rs
```
### 1.3 hello, Cargo!

```shell
cargo new
cargo build
cargo run
cargo check
cargo build --release
```

## 2. Programming a Guessing Game

* `prelude`
* `associated function`
* `reference`s are immutable by default.
* `enumeration`, often called an `enum`
* `variant`
* `SemVer`, Semantic Versioning
* `registry`
* `start..=end` inclusive on the lower and upper bounds
* `match` & `arm`
* `shadowing`


```shell
cargo doc --open
```


## 3. Coimmon Programming Concepts

### 3.1 Variables and Mutability

* constants & variables
    - `mut` cannot be used with constants
    - `const` keyword instead of `let`
    - type of the value *must* be annotated
    - costants may be set only to a constant expression

* Shadowing (`let`) & `mut` a variable
    - compile-time error without `let`; 
    - `let` can change the data type

### 3.2 Data Types

#### Scalar

* integers


    | Length | Signed | Unsigned |
    |:------ | :----- | :------- |
    | 8-bit  | `i8`   | `u8`     |
    | 16-bit | `i16`  | `u16`    |
    | 32-bit | `i32`  | `u32`    |
    | 64-bit | `i64`  | `u64`    |
    | 128-bit| `i128` | `u128`   |
    | arch   | isize  | usize    |
    
    
    | Number literals | Example |
    | :-------------- | :------ |
    | Decimal         | `98_222`|
    | Hex             | `0xff`  |
    | Octal           | `0o77`  |
    | Binary          | `0b1111_0000`|
    | Byte(`u8` only) | `b'A'`  |

    - `panicking`
    - `two's complement wrapping`
    - `wrapping_*`
    - `checked_*`
    - `overflowing_*`
    - `saturating_*`


* floating-point numbers
* Booleans
* characters


#### Compound

## Vocabulary
* arcane
* infamous
* lest
* customary
* fickle
* hassle
* endeavor
* smorgasbord 
    - [C] a mixture of many different hot and cold dishes that are arranged so that you can serve yourself （包含不同热菜和冷菜的）北欧式自助餐
    - [C usually singular] many different types of something that are offered 很多，大量（可供选择）a smorgasbord of choices
* crate 
* pincer
* insatiable
* nudge