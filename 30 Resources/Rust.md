# Resources

- [interactive rust book](https://rust-book.cs.brown.edu/)
- run `rustup doc` to get local access to 'the rust book' and 'rust by example.'
## Nice Tools
- `cargo fmt`
    - formats the code
- `cargo fix`
    - applies the compiler suggestions
- `cargo clippy`
    - further linting

# Language Features 

- Guaranteed Memory Safety
- if it compiles without unsafe mode code then it's saved:
    - variables must be initialised before you can use them.

# Syntax 

## Basic Structure
-   `fn` -- declares a function
-   `blah()` -- name of the function with arguments inside braces
-   `main()` -- main function is always the first code to run on every rust program
-    -- function bodies are always wrapped around b curley braces
-   `blah!()`-- calls a rust maro
-   end every line with `;`
-   `use::blah;` -- imports a library \'blah\'
-   `&var` -- references variable `var` instead of copying it

## Match

## Loops

```rust

```

## Error Handling

- `.expect("something")` -- crashes the programme and inserts the string into the error
- `Ok(something) => something(),` and `Err(something ) => something` handles error other wise
- `continue` means the program carries on without crashing.

## Variables

## Scope

- Variables local with the scope.

``` rust
fn main() {
    let x = 5;
    {
        let x = 99;
        println!("", x); //Print "99"
    }
    println!("", x); //Print "5"
}
```

scope for a variable is the block it's decleared in, a block nested in a parent block can call the variable int he parent block.

``` rust
fn main() {
    let x = 5;
    {
        let y = 99;
        println!(", ", x, y); //Print "5, 99"
    }
    println!(", ", x, y); //Error!
}
```

### No Garbage Collection
- *Stack frame* instead of *garbage collection.* Stack frames stacks the variables.
- when value goes out of scope, value will be dropped

### Variables are shadowed

- variables can be shadowed in the same scope and be redefined

``` rust
fn main() {
    let meme = "more cowbell!"; //x is mutable
    let meme = make_image(meme  ); // makes x immutable
}
```

using the `let` password, we can shaddow a vairable.

``` rust
fn main() {
    let x = 5;
    let x = x + 1;
    let x = x * 2;
    println!("the value of x is ", x);
}
```

x is effectively a brand new variable at each `let` call. so you can do things like

``` rust
fn main() {
    let spaces = "     ";
    let spaces = spaces.len();
    println!("there are  spaces.", spaces);
}
```

## Immutable variables

-   variables in rust are immutable by default
-   Variable sized things like string. have a pointer, a value and an *assigned capacity*.
-   when value goes out of scope, value will be dropped

### itterate over a vec and reture a new vec
```rust
fn vec_map(v: &Vec<i32>) -> Vec<i32> {
    v.iter().map(|element| {
      element * 2
    }).collect()
}
```
- note the .collect() function
# Basic Types

## Scalar Types

has a single value

1.  Ints

2.  Floats

3.  Char

## Compound types

1.  Tuple

    -   fixed length, can\'t grow or shrink in size
    -   can contain values of different types

    ``` rust
    fn main() {
        let tup = (500, 6.4, 1);

        // we can destructure tup with patern matching like this:
        let (_x, y, _z) = tup;
        println!("the value of y is ", y);
    }
    ```

    elements of the tuple can be accessed with the dot notation

    ``` rust
    fn main() {
        let x: (i32, f64, u8) = (500, 6.4, 1);
        let five_hundred = x.0;
        let six_point_four = x.1;
        let one = x.2;

        println!(
            "x.0 is , x.1 is , x.2 is ",
            five_hundred, six_point_four, one
        )
    }
    ```

2.  Arrays

    -   can only contain elements of the same type
    -   data on stack rather than heap

    ``` rust
    fn main() {
        let a = [1, 2, 3, 4];
        let months = [
            "January",
            "February",
            "March",
            "April",
            "May",
            "June",
            "July",
            "August",
            "September",
            "October",
            "November",
            "December",
        ];
        // type signature
        let a: [i32; 5] = [1, 2, 3, 4, 5];
        // another way to initialise arrays
        let b = [3; 5];
        // same as "let b = [3, 3, 3, 3, 3];"

        //accessing arrays
    }
    ```

# Functions

decleared like this

``` rust
fn do_stuff() 

fn do_stuff(qty: f64, unit_weight: f64) -> f64 {
    return qty * unit_weight;
    // can omit the key word 'return '. Tail calls
```

## Closures

``` rust
fn main() {
    let x = 4;

    let equal_to_x = |z| z == x;

    let y = 4;

    assert!(equal_to_x(y));
}
```

## Literals and Operators

``` rust
fn main() {
    // Integer addition
    println!("1 + 2 = ", 1u32 + 2);

    // Integer subtraction
    println!("1 - 2 = ", 1i32 - 2);
    // TODO ^ Try changing `1i32` to `1u32` to see why the type is important

    // Short-circuiting boolean logic
    println!("true AND false is ", true && false);
    println!("true OR false is ", true || false);
    println!("NOT true is ", !true);

    // Bitwise operations
    println!("0011 AND 0101 is ", 0b0011u32 & 0b0101);
    println!("0011 OR 0101 is ", 0b0011u32 | 0b0101);
    println!("0011 XOR 0101 is ", 0b0011u32 ^ 0b0101);
    println!("1 << 5 is ", 1u32 << 5);
    println!("0x80 >> 2 is 0x", 0x80u32 >> 2);

    // Use underscores to improve readability!
    println!("One million is written as ", 1_000_000u32);
}
```

## Symbols

| Sumbols          | example                   | What it does                          |
| ---------------- | ---------------           | ---------------                       |
| !                | `println!("hello world")` | denotes macros                        |
| ::               | `LinkedList::new`         | drill down into moduels functions etc |
| ;                | `println!("hello world")` | end every line with semicolon         |
| //               | `// this is a comment`    | comment                               |
| _                | `_`                       | denotes delibberate unused variables  |

## Ownership

-   [Video explaining ownership](https://www.youtube.com/watch?v=qrbbZ9_Sb68&feature=youtu.be)
-   Each value has an owner and only *one* owner.
-   value could be cloned.
-   \'&\' borrows a read only copy of the value in the scope
-   &mut, creates a mutable borrow



- Tooling 

- Rustup/ Shell commands

Installs and manages versions of rust.

``` shell
curl https://sh.rustup.rs -sSf | sh=
- fetch and runs the install script 
```


  Command                               what it does                         Notes
  ------------------------------------- ------------------------------------ -------------------------------
  `rustup update`            updates rust                         
  `rustup self uninstall`    Removes rust                         
  `rustup default nightly`   changes the build to nightly build   
  `rustup doc`               opens the documentation f or rust    
  `rustup doc --book`        Opens the rust book                  
  `rustfmt`                  formats the code                     
  `rustc`                    compiles the file,                   use cargo for larger projects

- Cargo

cargo coordinates the build

-   `cargo new` -- starts a new project
-   `cargo build` -- builds the project
-   `cargo run` -- compiles the project then runs the programme
-   `cargo check` -- checks that code compiles but does not produce an executable
-   `cargo build –release` -- compiles it for release, optimises the code. Program runs faster, but takes longer to compile
-   `cargo update` -- updates the packages to the latest
-   `cargo doc –open` -- builds and open all documentation of the dependencies.
-   `rustup docs` -- opens documentation. `–book` to open the guide.

- Cargo.toml

``` toml
[package]
name = "hello"
version ="0.1.0"
authors = ["name <address@mail.com>"]
edition = "2019"
[dependencies]
```

- Cargo script

``` bash
cargo install cargo-script
```

install for org-babel. If you\'ve got Cargo.el installed in your profile, you can evaluate pretty quick using Cargo-run. This may become how I write Rust going forward, if I can get flycheck to work too.

```
#+RESULTS:
```
- Crates

``` rust
extern crate rand;
//imports the crate, has to match Cargo.toml
```

- Example Code

- #+BEGIN~SRC~ rust

fn main() 

```
#+END_SRC
```
```
#+RESULTS:
```
``` example
hello world!
```

- Basic Function

``` rust
fn main() {
    let a = 1;
    let b = 2;
    println!(" +  is ", a, b, add(a, b));
}
fn add(a: i32, b: i32) -> i32 {
    return a + b;
}
```

- Imports and Name Spaces

``` rust
use std::collections::LinkedList;

fn main() {
    let mut ll = LinkedList::new();

    ll.push_back(1);
    ll.push_back(2);
    ll.push_back(3);

    for foo in ll {
        println!("", foo);
    }
}
```

- Fibbernacci

``` rust
const FIB_ZERO: u64 = 1;
const FIB_ONE: u64 = 1;

fn fib(n: u64) -> u64 {
    if n == 0 {
        FIB_ZERO
    } else if n == 1 {
        FIB_ONE
    } else {
        fib(n - 1) + fib(n - 2)
    }
}

fn main() {
    for i in 1..10 {
        println!(": ", i, fib(i))
    }
}
```

- Nth-Prime

-   can\'t seem to figure this out.

``` rust
fn main() {
    const FIRST_PRIME: u32 = 2;
    let mut primes: Vec<u32> = Vec::new();
    primes.push(FIRST_PRIME);
    println!("we have  primes", primes.len());

    fn find_next_prime(v: &Vec<u32>){
        count = v.pop()+1;
        for i in &v {
           if
        }
    }

    for i in &primes {
        println!(",", i)
    }
}
```

``` rust
 frmain() {
    let list_of_Prime = vec![2, 3, 5, 7, 11];
    let v: &i32 = &list_of_Prime[4];
    println!("last_prime = ", v)
}
```

- Types

Strong Stratic Typed

- Booleans

- Strings

- Enums

- Characters

- Libraries 

- Prelude

implicitly installed libraries including:

- std (standard library)

handles:

-   types and their operations
-   memory management
-   filesystems and I/O functions
-   basic networking
-   environment manipulation
-   multiprocessing support
-   collections
    -   sequences (Vec, LinkedList)
    -   Queue (VecDeque)
    -   Maps (HashMap, BtreeMap)
    -   Sets (HashSet, BtreeSet)

- TOKIO

- async io framework

- Yew

elm-like web application frame work that compiles to web-assembly

- Leptos

- full stack rust, blazingly fast

- [repo](https://github.com/gbj/leptos)

- Clap

- for

- Relm

rust gtk gui library with Elm Architecture <https://github.com/antoyo/relm>

- Pest

- general purpose parser

- <https://github.com/pest-parser/pest>

- <https://docs.rs/pest/latest/pest/https://docs.rs/pest/latest/pest/>

- Frameworks

- Rocket

Web framework <https://rocket.rs/>

- Amathyst Game Engin

<https://amethyst.rs/>

- Resources

- Key Words

\*

- Resources

- Examples

- <https://github.com/abhimanyu003/qubit>

1.  cool web based calculator, could learn a lot and extend fro this

- Books

- [Rust Book (Where I\'m at)](https://doc.rust-lang.org/book/ch01-02-hello-world.html) - The official Intro. Should take about 2 weeks. -

Start with this. - could also use the commnd `rustup docs --book` to access it offline

- Rust Cookbook

<https://rust-lang-nursery.github.io/rust-cookbook/>

- Rust Cli Apps

\-<https://rust-cli.github.io/book/index.html>

- Rust By example

<https://doc.rust-lang.org/rust-by-example/>

- Book list

<https://github.com/sger/RustBook> s

- [programming rust](https://learning-oreilly-com.ezproxy.christchurchcitylibraries.com/library/view/programming-rust/9781491927274/)

- Rust Web Programming

<https://learning-oreilly-com.ezproxy.christchurchcitylibraries.com/library/view/rust-web-programming/9781800560819/>

- Excerciese

-   [Rustlings](https://github.com/rust-lang/rustlings/)
    -   coding Excercises
-   Excercism (stuck on primes, read the below2) <https://medium.com/@omenlogo/primes-numbers-in-elm-259a8ac1300f>

- Videos

-   <https://learning-oreilly-com.ezproxy.christchurchcitylibraries.com/videos/learning-rust/9781788477918/continue>
-   [Rust~101~](https://www.youtube.com/watch?v=FMqydRampuo)
    -   the video in the Wikipedia article
-   [You Code Things](https://www.youtube.com/channel/UC0yCXVwW6FdDQGYA-3OWXxw)
    -   Youtube channel with fairly fun and concise intro vids (good overview of some concepts)
-   [Hello Rust](https://www.youtube.com/channel/UCZ_EWaQZCZuGGfnuqUoHujw/videos)
-   [Tensor Programming Course](https://www.youtube.com/watch?v=EYqceb2AnkU&list=PLJbE2Yu2zumDF6BX6_RdPisRVHgzV02NW)
    -   Runs through the basics, till building API and connecting to elm
-   <https://hackr.io/tutorials/learn-rust>

- Others

-   <https://speakerdeck.com/jvns/learning-systems-programming-with-rust?slide=13>
-   <http://www.arewewebyet.org/>
