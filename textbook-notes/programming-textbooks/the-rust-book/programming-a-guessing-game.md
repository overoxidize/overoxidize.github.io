+++
title = "Programming A Guessing Game"
tags = ["rust", "programming"]
+++

#### Setting Up A New Project:

To generate a new Rust project use the following command: 

`cargo new <project-name>`.

### New Rust projects will have a minimal Cargo.[toml]([[Toms Ordinary Markup Language) file.

### Cargo.toml:


```Rust 
[package]
name = "guessing_game"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
edition = "2018"

[dependencies]
```


#### Processing A Guess:

```Rust use std::io;

fn main() {
    println!("Guess the number!");

    println!("Please input your guess.");

    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    println!("You guessed: {}", guess);
}```

By default, Rust will bring only a few types into scope in the prelude, so if you want a type that isn't available in the prelude, you have to add it yourself, with the `use <type>` statement.

## Storing Values with Variables:

`let mut guess = String::new();`

__A mutable variable guess bound to a new empty instance of String.__

You can declare a variable with the `let` keyword, and make it mutable with the `mut` keyword.

The `::new()` syntax indicates that an associated function that exists on a type is being called. `new` exists on mosts types, for creating new values of certain times.

#### Receiving Input

Using std::io allows us to access code from the module that allows us to deal with input an output, and it provides the Read and Write traits, which can be implemented in other types.

The `read_line(&mut guess)` line helps us read the input from out terminal, the stdin, and it allows us to store that input in our mutable variable, which we indicate is a reference to a mutable variable with the `&mut` syntax.

References in Rust are perhaps similar but not exactly like references in the context of 'pass by reference', but they allow multiple parts of code to access a datum without copying it into memory each time.

The `read_line` function returns a value, of the type io::Result.

**__Result__** types are __enums__, meaning they can be one of a discrete, finite set of values, which are referred to as __variants__.

The `Result` variants, are `Ok`, and `Err`.

`Ok`, indicates the operation was successful, `Err` contains information on how/why it wasn't.

Instances of `Result` have `expect` methods that can be called, causing the program to crash and display your message.

If the value is `Ok`, `expect` will simply return it to you.

#### Using Crates to Get More Functionality:

Crates are collections of Rust source, and this project is a __binary__ crate, intended to be an executable, but there are also library crates, such as `rand`, which are intended to be used in building binary crates.

Crates such as these, are added to the Cargo.toml file as dependencies.

Rust handles versioning of project dependencies with semver.

Most crates in the Rust ecosystem are stored in Crates.io, the registry for libraries.

Cargo will not only grab your dependencies, but any required upstream dependencies that those depend on as well.

The **__Cargo.lock__** file is for producing builds that can run on other computers, even if changes in the dependencies take places, and are on a new SemVer than the ones your project depends on.

`cargo update` will update all of the out of date dependencies in your Cargo.toml file, but 

#### Comparing Guesses:

```Rust use rand::Rng;
use std::cmp::Ordering;
use std::io;

fn main() {
    // --snip--

    println!("You guessed: {}", guess);

    match guess.cmp(&secret_number) {
        Ordering::Less => println!("Too small!"),
        Ordering::Greater => println!("Too big!"),
        Ordering::Equal => println!("You win!"),
    }
}```

In this code, we use the :: syntax to bring types outside of the scope of the prelude into local scope for use.

`Ordering`, is an enum, meaning it "contains" several variants, (more technically, can be of the type of one of several variants), which are `Greater`, `Less`, and `Equal`.

Here the `cmp` method will compare the value it's given, with the value it was called on, and will return one of the `Ordering` variant types, which match will then compare with the arm's of it's body.

`match` : the arms consist of patterns and the code to be executed upon a match between a pattern and a value.

While Rust does have a strong static type system, it also has type inference, for instance, we didn't have to indicate guess was a string.
