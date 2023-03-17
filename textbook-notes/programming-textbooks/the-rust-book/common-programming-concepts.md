+++
title = "Common Programming Concepts"
tags = ["rust"]
+++


__Keywords__: Rust as a set of keywords currently in use, and reserved for future use.

# Variables and Mutability:

Variables in rust are immutable, but you can make your variables mutable, by adding the `mut` keyword in front of them.

```Rust 
fn main() {
    let x = 5;
    println!("The value of x is: {}", x);
    x = 6;
    println!("The value of x is: {}", x);
}```

This code will throw a compile-time error, as x is an immutable variable, and we've not used the required keyword to indicate (to the compiler) that we want this valuable to be subject to change over time. 

`let mut x = 5` will remove the error.

# Variables vs Constants:

Rust provides a construct for constant variables, via the `const` keyword. __Note: when using__ `const` __the type of the value must be annotated.__

### Constants cannot be set to a value that can only be computed at run-time.

`const MAX_POINTS: u32 = 100_000;`.

# Shadowing:

When you declare a variable with the same name as a previous variable, the first variable is said to be shadowed by the second, indicating that the second variable's value is what is seen when the variable is used.

Shadowing can be initiated by reusing a variable name with the let keyword.

```Rust
let x = 5;

let x = x * x;
```

Shadowing differs from making a variable mutable, because we'll get a compile-time error if we try to reassign the variable without using the `let` keyword.

The other difference is that we're effectively creating a new variable when we use the `let` keyword, allowing us to change the type of a value but use the same name.

# Data Types:

### Every value in rust of a certain data type.

### Rust is statically typed, so it must know the types of all __variables__ at compile time.

## Scalar Types:

A scalar type represent a single value, and in Rust there are: integers, floats, booleans, and chars.

## Unsigned Integers: / Signed Integers:

An integer is a whole number, and is associated with the `__u32__` type. `u` and `i` will denote a unsigned or signed integer respectively.

The bit size ranges from 8-128, and an additional `size` for 32/64 bit systems.

Floats:

Floats are for representing decimals, and come as 32 by default, but have 64 as well.

Char:

Rust's char type is 4 bytes, and is unicode, meaning it extends beyond ascii, including emoji, etc.

Compound Types:

### Tuples:

A tuple is a way of grouping together values of varied types, and are fixed length structures.

```Rust fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
}```

Tuples can be destructured via pattern matching:

```Rust fn main() {
    let tup = (500, 6.4, 1);

    let (x, y, z) = tup;

    println!("The value of y is: {}", y);
}```

Tuple indexes are accessed via dot notation, and the numerical index, i.e `tuple.1`.

### Arrays:

Rust arrays must have same type elements, and are fixed length as well.

They are useful for allocating data on the stack, rather than the heap.

Similar to arrays, are vectors, that can grow or shrink in size.

Functions:

Rust has a take on expressions vs. statements:

Statements are instructions that perform actions, but don't return values.

Expressions evaluate to a value. 

In some languages, assignments return the value assigned, but this is not true in Rust, so you can't do `let y = (let x = 7)`, as `let x = 7` doesn't return a value, so there's nothing to bind y to.

If you add a semicolon to the end of an expression, you render it a statement, and thus it won't return a value.

Functions return the value of the final expression in them, or whenever return is encountered.

# Control Flow:

Note that you can use if's in `let` statements, because they are expressions (they evaluate to a value).

```Rust 
fn main() {
    let condition = true;
    let number = if condition { 5 } else { 6 };

    println!("The value of number is: {}", number);
}```

## **Repetition with Loops**:

## Rust provides several loop constructs for executing code more than once: loop, while, and for.

## **Returning values from Loops**:

## Loop is useful for, say, retrying operations that might fail, such as checking whether a thread has completed its job, but you might also need to pass that result to higher or lower levels of abstraction in your code.

## You can use `break` followed by your desired return value, to exit a loop and return it.

