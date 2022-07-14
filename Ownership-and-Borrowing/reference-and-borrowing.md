# Reference
1. Question:
```rust
fn main() {
   let x = 5;
   // Fill the blank
   let p = __;

   println!("the memory address of x is {:p}", p); // One possible output: 0x16fa3ac84
}
```
Answer:
```rust
fn main() {
   let x = 5;
   let p = &x;
   println!("the memory address of x is {:p}", p);
}
```
---
2. Question:
```rust
fn main() {
    let x = 5;
    let y = &x;

    // Modify this line only
    assert_eq!(5, y);

    println!("Success!");
}
```
Answer:
```rust
fn main() {
    let x = 5;
    let y = &x;
    assert_eq!(5, *y);
    println!("Success!");
}
```
---
3. Question:
```rust
// Fix error
fn main() {
    let mut s = String::from("hello, ");

    borrow_object(s);

    println!("Success!");
}

fn borrow_object(s: &String) {}
```
Answer:
```rust
fn main() {
    let mut s = String::from("hello, ");
    borrow_object(&s);
    println!("Success!");
}
fn borrow_object(s: &String) {}
```
---
4. Question:
```rust
// Fix error
fn main() {
    let mut s = String::from("hello, ");

    push_str(s);

    println!("Success!");
}

fn push_str(s: &mut String) {
    s.push_str("world")
}
```
Answer:
```rust
fn main() {
    let mut s = String::from("hello, ");
    push_str(&mut s);
    println!("Success!");
}
fn push_str(s: &mut String) {
    s.push_str("world")
}
```
---
5. Question:
```rust
fn main() {
    let mut s = String::from("hello, ");

    // Fill the blank to make it work
    let p = __;
    
    p.push_str("world");

    println!("Success!");
}

```
Answer:
```rust
fn main() {
    let mut s = String::from("hello, ");
    let p = &mut s;
    p.push_str("world");
    println!("Success!");
}
```
---
6. Question:
```rust
fn main() {
    let c = '中';

    let r1 = &c;
    // Fill the blank，dont change other code
    let __ r2 = c;

    assert_eq!(*r1, *r2);
    
    // Check the equality of the two address strings
    assert_eq!(get_addr(r1),get_addr(r2));

    println!("Success!");
}

// Get memory address string
fn get_addr(r: &char) -> String {
    format!("{:p}", r)
}

```
Answer:
```rust
fn main() {
    let c = '中';
    let r1 = &c;
    let ref r2 = c;
    assert_eq!(*r1, *r2);
    assert_eq!(get_addr(r1),get_addr(r2));
    println!("Success!");
}
fn get_addr(r: &char) -> String {
    format!("{:p}", r)
}
```
---
# Borrowing rules
7. Question:
```rust
// Remove something to make it work
// Don't remove a whole line !
fn main() {
    let mut s = String::from("hello");

    let r1 = &mut s;
    let r2 = &mut s;

    println!("{}, {}", r1, r2);

    println!("Success!");
}

```
Answer:
```rust
// Remove something to make it work
// Don't remove a whole line !
fn main() {
    let s = String::from("hello");
    let r1 = & s;
    let r2 = & s;
    println!("{}, {}", r1, r2);
    println!("Success!");
}
```
---
8. Question:
```rust
fn main() {
    // Fix error by modifying this line
    let  s = String::from("hello, ");

    borrow_object(&mut s);

    println!("Success!");
}

fn borrow_object(s: &mut String) {}
```
Answer:
```rust
fn main() {
    let mut s = String::from("hello, ");
    borrow_object(&mut s);
    println!("Success!");
}
fn borrow_object(_s: &mut String) {}
```
---
9. Question:
```rust
// This code has no errors!
fn main() {
    let mut s = String::from("hello, ");

    borrow_object(&s);
    
    s.push_str("world");

    println!("Success!");
}

fn borrow_object(s: &String) {}
```
Answer:
```rust
fn main() {
    let mut s = String::from("hello, ");
    borrow_object(&mut s); 
    s.push_str("world");
    println!("Success!");
}
fn borrow_object(_s: &String) {}
```
---
# NLL
10. Question:
```rust
// Comment one line to make it work
fn main() {
    let mut s = String::from("hello, ");

    let r1 = &mut s;
    r1.push_str("world");
    let r2 = &mut s;
    r2.push_str("!");
    
    println!("{}",r1);
}

```
Answer:
```rust
fn main() {
    let mut s = String::from("hello, ");
    let r1 = &mut s;
    r1.push_str("world");
    let r2 = &mut s;
    r2.push_str("!");
    // println!("{}",r1);
}
```
---
11. Question:
```rust
fn main() {
    let mut s = String::from("hello, ");

    let r1 = &mut s;
    let r2 = &mut s;

    // Add one line below to make a compiler error: cannot borrow `s` as mutable more than once at a time
    // You can't use r1 and r2 at the same time
}
```
Answer:
```rust
fn main() {
    let mut s = String::from("hello, ");
    let r1 = &mut s;
    let r2 = &mut s;
    r1.push_str("world");
}
```
---