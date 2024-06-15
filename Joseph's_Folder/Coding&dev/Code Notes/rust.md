# Rust    
This is the start of my rust programming journey.   
begun rust on 05.09.2023.   
   
Rust is a low-level programming language and is used very widely because of how loved the language is. Rust is different from C and C++ especially because it has no classes or Object Oriented Programming (OOP) in general. It is also very well known to be memory-safe (less chance of destroying your computer) and different. I am very excited to see how this goes.   
```
fn main() {
    println!("Hello World!");
    println!("I am learning RUST!\n");
}
```
First Hello World program in Rust.   
OK. I have collected some info on rust.    
I have been working with cargo a lot recently. cargo is Rust's package & build manager. It is used to make the blueprint of how a build will work, build it together, and install "dependencies" for code to run. The Cargo.toml file is usually what determines what cargo does including what dependencies it installs.    
I use "cd", A very common Unix OS command (especially BASh) to open a directory. I start by just using "cd" so that I can go back to my login directory, " ~User/USERNAME/". I then use "User/USERNAME/code/Rust/ " to decide where cargo is going to make a new project. I then use cargo new FILE\_NAME and then it will build a new rust project in that directory. "cargo build" will then build that project and install dependencies that the code needs. You also use the "cargo run" just to run the "main.rs" file in the "src" directory. This will just compile and give you a warning using Rust's powerful compiler if things go wrong.   
### Guessing game :    
This is the entry to the guessing game. I'll be following the official "Rust Programming Book".    
Building a simple guessing game where the computer will generate a number and the user will try to guess it. 
We will be using Random and Standard crates to generate a pseudo-random number and also to input user data.    
```
use rand::Rng;
use std::io;

fn main() {
    println!("WELCOME to Guess The Number!");

    // Random number generator using the rand crate from cargo.
    let secret_number = rand::thread_rng().gen_range(1..=100);
    println!("The random number has been generated. ");
    println!("Your secret number is {secret_number}!");

    println!("Please input your number : ")
    let mut user_guess = String::new();
    io::stdin()
        .read_line(&mut user_guess)
        .expect("Failed to read line ");
```
- To declare a variable, the "let" keyword is used. All variables are immutable (unchangeable by default) but by using "mut" you can make a cariable mutable and thus during it's life time, its values can be changed.     
- Returning to the guessing game program, you now know that `let mut guess` will introduce a mutable variable named `guess`. The equal sign ( `=`) tells Rust we want to bind something to the variable now. On the right of the equal sign is the value that `guess` is bound to, which is the result of calling `String::new`, a function that returns a new instance of a `String`. `[String](../std/string/struct.String.html)` is a string type provided by the standard library that is a growable, UTF-8 encoded bit of text.   
- The `::` syntax in the `::new` line indicates that `new` is an associated function of the `String` type. An *associated function* is a function that’s implemented on a type, in this case `String`. This `new` function creates a new, empty string. You’ll find a `new` function on many types because it’s a common name for a function that makes a new value of some kind.   
- In full, the `let mut guess = String::new();` line has created a mutable variable that is currently bound to a new, empty instance of a `String`. Whew!   
   
   
Recall that we included the input/output functionality from the standard library with `use std::io;` on the first line of the program. Now we’ll call the `stdin` function from the `io` module, which will allow us to handle user input:   
```
    io::stdin()
        .read_line(&mut guess)

```
If we hadn’t imported the `io` library with `use std::io;` at the beginning of the program, we could still use the function by writing this function call as `std::io::stdin`. The `stdin` function returns an instance of `[std::io::Stdin](../std/io/struct.Stdin.html)`, which is a type that represents a handle to the standard input for your terminal.   
The `&` indicates that this argument is a *reference*, which gives you a way to let multiple parts of your code access one piece of data without needing to copy that data into memory multiple times. References are a complex feature, and one of Rust’s major advantages is how safe and easy it is to use references. You don’t need to know a lot of those details to finish this program. For now, all you need to know is that, like variables, references are immutable by default. Hence, you need to write `&mut guess` rather than `&guess` to make it mutable. (Chapter 4 will explain references more thoroughly.)   
   
