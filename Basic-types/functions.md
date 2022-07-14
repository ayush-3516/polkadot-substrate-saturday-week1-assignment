1. Question:
```rust
fn main() {
    // Don't modify the following two lines!
    let (x, y) = (1, 2);
    let s = sum(x, y);

    assert_eq!(s, 3);

    println!("Success!");
}

fn sum(x, y: i32) {
    x + y;
}

```
Answer:
```rust
fn main() {
    let (x, y) = (1, 2);
    let s = sum(x, y);
    assert_eq!(s, 3);

    println!("Success!");
}

fn sum(x: i32, y: i32) {
    x + y
}
output: Success!
solution: added datatype i32 to x in the parameters for sum() and removed the semi colon to return the sum
```
---
2. Question:
```rust
fn main() {
   print();
}

// Replace i32 with another type
fn print() -> i32 {
   println!("Success!");
}
```
Answer:
```rust
fn main() {
   print();
}

fn print() -> () {
   println!("Success!");
}
output: Success!
solution: corrected i32 to () because it was not the return type for the function
```
---
3. Question:
```rust
// Solve it in two ways
// DON'T let `println!` works
fn main() {
    never_return();

    println!("Failed!");
}

fn never_return() -> ! {
    // Implement this function, don't modify the fn signatures
    
}
```
Answer:
```rust
fn main() {
    never_return();
}

fn never_return() -> ! {
    // implement this function, don't modify fn signatures
    panic!("This returns nothing")
}
output: thread 'main' panicked at 'This returns nothing', helloworld.rs:7:5
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace

solution: added a panic statement to remove unwanted printlns
```
```rust
fn main() {
    never_return();
}

use std::thread;
use std::time;

fn never_return() -> ! {
    // implement this function, don't modify fn signatures
    loop {
        println!("I return nothing");
        // sleeping for 1 second to avoid exhausting the cpu resoucre
        thread::sleep(time::Duration::from_secs(1))
    }
}
```
---
4. Question:
```rust
fn main() {
    println!("Success!");
}

fn get_option(tp: u8) -> Option<i32> {
    match tp {
        1 => {
            // TODO
        }
        _ => {
            // TODO
        }
    };
    
    // Rather than returning a None, we use a diverging function instead
    never_return_fn()
}

// IMPLEMENT this function in THREE ways
fn never_return_fn() -> ! {
    
}
```
Answer:
```rust
fn main() {
    println!("Success!");
}
fn get_option(tp: u8) -> Option<i32> {
    match tp {
        1 => {
            // TODO
        }
        _ => {
            // TODO
        }
    };

    never_return_fn()
}
fn never_return_fn() -> ! {
    unimplemented!()
}
output: Success!
```
```rust
fn main() {
    println!("Success!");
}
fn get_option(tp: u8) -> Option<i32> {
    match tp {
        1 => {
            // TODO
        }
        _ => {
            // TODO
        }
    };

    never_return_fn()
}
fn never_return_fn() -> ! {
    panic!()
}
```
```rust
fn main() {
    println!("Success!");
}
fn get_option(tp: u8) -> Option<i32> {
    match tp {
        1 => {
            // TODO
        }
        _ => {
            // TODO
        }
    };

    never_return_fn()
}
fn never_return_fn() -> ! {
    loop {
        std::thread::sleep(std::time::Duration::from_secs(1))
    }
}
```
---
5. Question:
```rust
fn main() {
    // FILL in the blank
    let b = __;

    let v = match b {
        true => 1,
        // Diverging functions can also be used in match expression to replace a value of any value
        false => {
            println!("Success!");
            panic!("we have no value for `false`, but we can panic");
        }
    };

    println!("Exercise Failed if printing out this line!");
}
```
Answer:
```rust
fn main() {
    let b = false;
    let _v = match b {
        true => 1,
        false => {
            println!("Success!");
            panic!("we have no value for `false`, but we can panic");
        }
    };
    println!("Exercise Failed if printing out this line!");
}

output: Success!
thread 'main' panicked at 'we have no value for `false`, but we can panic', helloworld.rs:7:13
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
solution: added false to b and corrected v as _v
```