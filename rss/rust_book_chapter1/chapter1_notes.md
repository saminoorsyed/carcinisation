# Chapter 1 notes

## Anatomy of a Rust program

```
fn main() {
}
```
The main function is special: it is alsways the first code that runs in every executable Rust program. The above has no parameters and returns nothing.


The function body is always wrapped in {}. the reccomended style is to place the opening { after the parameters on the same line as the function declaration with once space inbetween

```
    println!("Hello, World");
```

### four key components:

1. Rust style is to indent with four spaces, not a tab

2. ``` println!``` calls a Rust macro. if it were a function instead of a macro, ti would not include the ```!``` at the end of the call.

3. The "Hello, World" string is passed as an arg to the macro and printed to the screen

4. the line ends with a ```;``` which indicates that the expression is over and the next is ready to begin

### Compiling and Running are separate steps

after writing a new program there are a few steps you must complete before running the program

first you must run rustc main.rs

This outputs a binary executable simply run the program by typing ./main

executables can be run without a rust installation, will run fine on any system

## Hello Cargo!

Cargo is rusts build system and package manager:
builds code, downloads libraries and builds those libraries (dependencies)

starting a project using cargo will make adding dependencies later on much easier to do.

```$ cargo new hello_cargo ```
```$ cd hello_cargo ```

the first creates a new direcoty and project containing two files a Cargo.toml and src directory with a main.rs

there is also a new git repository along with a .gitignore file (the git files wwon't gen if you run cargo new inside an existing Git repository. can override with new --vcs=git )

### Within cargo.toml

1. ```[package]``` is a section heading that indicate that the following statements are configuring a package
2. the next three lines set the configuration info cargo needs to compile your program, the name, version and edition  of trust to use
3. ```[dependencies]``` this is the start of the section for you to list any of your projects dependencies, or ***cratres*** 

### inside the src directory

Cargo expects your source files to live inside the src directory. the top level directory is just for readme files, licelse information, config fiels and anything not related to your actual code. With Cargo, everything has its place.

if you have a project that you did not start with Cargo, it is trivial to add the above elements and move your code to the src file.

### Building and Running a Cargo Project

build your project by entering the following command:

$ cargo build
This command creates an executable file in target/debug/hello_cargo 

run the file with the following:
```$ ./target/debug/hello_cargo```

Running cargo build for the first time also causes Cargo to create a new file at the top level: Cargo.lock. This file keeps track of the exact versions of dependencies in your project

we can also use cargo run to compile the code and then run the resultant executable all in one command:
```
$ cargo run
```
Using cargo run is more convenient than having to remember to run cargo build and then use the whole path to the binary, so most developers use cargo run.

this time we didn’t see output indicating that Cargo was compiling hello_cargo. Cargo figured out that the files hadn’t changed, so it didn’t rebuild but just ran the binary. If you had modified your source code, Cargo would have rebuilt the project before running it

Cargo also provides a command called cargo check. This command quickly checks your code to make sure it compiles but doesn’t produce an executable:
```
$ cargo check
```
cargo check is much faster than cargo build because it skips the step of producing an executable

### Building for Release

When your project is ready for release you can use:

```
cargo build --release
```

this will create an executable in the target/release instead of target/debug

this build takes longer to compile, but the optomizations will make your code run faster. the debug build is quicker, but doesn't have those optomizations

to benchmark your codes running time use :

```
cargo build --release
```
and use that executable for a benchmark

here is a link to Cargo documentation:

https://doc.rust-lang.org/cargo/
