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
2. Question:
```rust
//  Fill the blank
fn main() {
    let v: u16 = 38_u8 as __;

    println!("Success!");
}

```
Answer:
```rust
fn main() {
    let v: u16 = 38_u8 as u16;

    println!("Success!");
}
output: Success!
solution: added u16
```
---
3. Question:
```rust
// Modify `assert_eq!` to make it work
fn main() {
    let x = 5;
    assert_eq!("u32".to_string(), type_of(&x));

    println!("Success!");
}

// Get the type of given variable, return a string representation of the type  , e.g "i8", "u8", "i32", "u32"
fn type_of<T>(_: &T) -> String {
    format!("{}", std::any::type_name::<T>())
}
```
Answer:
```rust
// Modify `assert_eq!` to make it work
fn main() {
    let x = 5;
    assert_eq!("i32".to_string(), type_of(&x));

    println!("Success!");
}

// Get the type of given variable, return a string representation of the type  , e.g "i8", "u8", "i32", "u32"
fn type_of<T>(_: &T) -> String {
    format!("{}", std::any::type_name::<T>())
}
output: Success!
solution: corrected u32 to i32
```