1. Question:
```rust
// Fix the errors, DON'T add new lines!
fn main() {
    let arr = [1, 2, 3];
    let s1: [i32] = arr[0..2];

    let s2: str = "hello, world" as str;

    println!("Success!");
}
```
Answer:
```rust
fn main() {
    let arr = [1, 2, 3];
    let _s1: &[i32] = &arr[0..2];
    let _s2: &str = "hello, world";
    println!("Success!");
}
```
---
2. Question:
```rust

fn main() {
    let arr: [char; 3] = ['中', '国', '人'];

    let slice = &arr[..2];
    
    // Modify '6' to make it work
    // TIPS: slice( reference ) IS NOT an array, if it is an array, then `assert!` will passed: Each of the two UTF-8 chars '中' and '国'  occupies 3 bytes, 2 * 3 = 6
    assert!(std::mem::size_of_val(&slice) == 6);

    println!("Success!");
}
```
Answer:
```rust
fn main() {
    let arr: [char; 3] = ['中', '国', '人'];
    let slice = &arr[..2];
    assert!(std::mem::size_of_val(&slice) == 16);
    println!("Success!");
}
```
---
3. Question:
```rust
```
Answer:
```rust
```
---
4. Question:
```rust
```
Answer:
```rust
```
---
5. Question:
```rust
```
Answer:
```rust
```
---
6. Question:
```rust
```
Answer:
```rust
```
---