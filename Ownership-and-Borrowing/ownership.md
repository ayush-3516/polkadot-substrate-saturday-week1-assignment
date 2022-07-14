# Ownership
1. Question:
```rust
fn main() {
    // Use as many approaches as you can to make it work
    let x = String::from("hello, world");
    let y = x;
    println!("{},{}",x,y);
}
```
Answer:
```rust
fn main() {
    let x = String::from("hello, world");
    let y = x.clone();
    println!("{},{}",x,y);
}
output: hello, world,hello, world
solution: used clone function to clone x into y
```
---
2. Question:
```rust
// Don't modify code in main!
fn main() {
    let s1 = String::from("hello, world");
    let s2 = take_ownership(s1);
    println!("{}", s2);
}
// Only modify the code below!
fn take_ownership(s: String) {
    println!("{}", s);
}
```
Answer:
```rust
fn main() {
    let s1 = String::from("hello, world");
    let s2 = take_ownership(s1);
    println!("{}", s2);
}
fn take_ownership(s: String) -> String{
    println!("{}", s);
    s
}
output: hello, world
        hello, world
solution: adding String returning datatype to take_ownership and returning s from it 
```
---
3. Question:
```rust
fn main() {
    let s = give_ownership();
    println!("{}", s);
}
// Only modify the code below!
fn give_ownership() -> String {
    let s = String::from("hello, world");
    // Convert String to Vec
    let _s = s.into_bytes();
    s
}
```
Answer:
```rust
fn main() {
    let s = give_ownership();
    println!("{}", s);
}
fn give_ownership() -> String {
    let s = String::from("hello, world");
    let _s = s.as_bytes();
    s
}
output: hello, world
solution: corrected s.into_bytes() to s.as_bytes()
```
---
4. Question:
```rust
// Fix the error without removing code line
fn main() {
    let s = String::from("hello, world");

    print_str(s);

    println!("{}", s);
}

fn print_str(s: String)  {
    println!("{}",s)
}

```
Answer:
```rust
fn main() {
    let s = String::from("hello, world");
    print_str(s.clone());
    println!("{}", s);
}
fn print_str(s: String)  {
    println!("{}",s)
}
output: hello, world
        hello, world
solution: used to clone function for print_str
```
---
5. Question:
```rust
// Don't use clone ,use copy instead
fn main() {
    let x = (1, 2, (), "hello".to_string());
    let y = x.clone();
    println!("{:?}, {:?}", x, y);
}
```
Answer:
```rust
fn main() {
    let x = (1, 2, (), "hello");
    let y = x;
    println!("{:?}, {:?}", x, y);
}
output: (1, 2, (), "hello"), (1, 2, (), "hello")
solution: removed to_string method from the x parameter because it was already a string and corrected y = x.clone() as y = x
```
---
## Mutability
6. Question:
```rust
fn main() {
    let s = String::from("hello, ");
    
    // Modify this line only !
    let s1 = s;

    s1.push_str("world");

    println!("Success!");
}

```
Answer:
```rust
fn main() {
    let s = String::from("hello, ");
    let mut s1 = s;
    s1.push_str("world");
    println!("Success!");
}
output: Success!
solution: added mut to s1
```
---
7. Question:
```rust
fn main() {
    let x = Box::new(5);
    
    let ...      // Implement this line, dont change other lines!
    
    *y = 4;
    
    assert_eq!(*x, 5);

    println!("Success!");
}

```
Answer:
```rust
fn main() {
    let x = Box::new(5);
    let mut y = Box::new(3);
    *y = 4;
    assert_eq!(*x, 5);
    println!("Success!");
}
output: Success!
solution: added mut y = Box::new(3);
```
---
## Parital Move
8. Question:
```rust
fn main() {
   let t = (String::from("hello"), String::from("world"));

   let _s = t.0;

   // Modify this line only, don't use `_s`
   println!("{:?}", t);
}

```
Answer:
```rust
fn main() {
   let t = (String::from("hello"), String::from("world"));
   let _s = t.0;
   println!("{:?}", t.1);
}
output: "world"
solution: corrected t to t.1 to print the second element of t
```
---
9. Question:
```rust
fn main() {
   let t = (String::from("hello"), String::from("world"));

    // Fill the blanks
    let (__, __) = __;

    println!("{:?}, {:?}, {:?}", s1, s2, t); // -> "hello", "world", ("hello", "world")
}

```
Answer:
```rust
fn main() {
    let t = (String::from("hello"), String::from("world"));
    let (s1, s2) = t.clone();
    println!("{:?}, {:?}, {:?}", s1, s2, t);
}
output: "hello", "world", ("hello", "world")
solution: using the clone of t to store in (s1, s2)
```
---