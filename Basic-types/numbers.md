# Integer
1. Question: 
```rust

// Remove something to make it work
fn main() {
    let x: i32 = 5;
    let mut y: u32 = 5;

    y = x;
    
    let z = 10; // Type of z ? 

    println!("Success!");
}
```
Answer: 
```rust
fn main(){
    let x: i32 = 5;
    let mut y: u32 = 5;

    let z = 10; // Type of z ? 

    println!("Success!");
}

output: Success!
solution: removed the y = x; line
```
---
