+++
title = "Getting Started"
tags = ["rust"]
+++

## Anatomy Of a Rust Program

```Rust
fn main() {
	println!("Hello, world!");
}
```
Rust, like many other languages, has a special main function, which is the first function that runs in any Rust program.

println! calls a Rust #macro. 

! indicates calling a #macro as opposed to a normal function.

Before you run a Rust program, it must be compiled, using the Rust compiler, and the `rustc` command, to which a file is given as an argument.

Rust is AOT compiled, meaning if you compile a program and give it to someone, they can execute it without having Rust installed.

## Hello, Cargo!

[[Cargo]] is Rust's build system and package manager.

Cargo uses [TOML]([[Toms Ordinary Markup Language]]), as it's configuration format.

### Filename: Cargo.toml:

```Rust
[package]
name = "hello_cargo"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
edition = "2018"
[dependencies]
```

`[package]` is a heading that indicates the following statements configure a package.

The next four lines (2-5), set the config info Cargo needs to compile a program- the name, version, author, and Rust edition to use.

`[dependencies]`, is the start of a section to list project dependencies. 

In #Rust, packages of code are called crates.  

### __Use__ `cargo build` __to build your program.__

This command generates an executable file.

The first time you run the build command, a Cargo.lock file is generated to keep track of dependency versioning.

### __Use__ `cargo run` __to compile and run the resulting executable in consecutively.__

Cargo can tell if source files have changed, and will not attempt to rebuild a program with an existing binary if the source code hasn't changed.

### __Use__ `cargo check` to __make sure your code will compile (without generating an executable).__

### When your project is ready for release, use `cargo build --release` to compile it with optimizations.

