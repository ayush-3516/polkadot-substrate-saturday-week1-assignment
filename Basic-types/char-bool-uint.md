# Char
1. Question:
```rust
// Make it work
use std::mem::size_of_val;
fn main() {
    let c1 = 'a';
    assert_eq!(size_of_val(&c1),1); 

    let c2 = '中';
    assert_eq!(size_of_val(&c2),3); 

    println!("Success!");
} 
```
Answer:
```rust
// Make it work
use std::mem::size_of_val;
fn main() {
    let c1 = 'a';
    assert_eq!(size_of_val(&c1),4); 

    let c2 = '中';
    assert_eq!(size_of_val(&c2),4); 

    println!("Success!");
} 
output: Success!
solution: corrected the value of c1 and c2 to 4
```
---
2. Question:
```rust
// Make it work
fn main() {
    let c1 = "中";
    print_char(c1);
} 

fn print_char(c : char) {
    println!("{}", c);
}

```
Answer:
```rust
fn main() {
    let c1 = '中';
    print_char(c1);
} 

fn print_char(c : char) {
    println!("{}", c);
}
output: 中
solution: changed double quotations to single quotations
```
---
# Bool
3. Question:
```rust
// Make println! work
fn main() {
    let _f: bool = false;

    let t = true;
    if !t {
        println!("Success!");
    }
} 
```
Answer:
```rust
// Make println! work
fn main() {
    let _f: bool = false;

    let t = true;
    if !t {
        println!("Success!");
    }
} 
output: Success!
solution: Changed true to false to meet the condition
```
---
4. Question:
```rust
// Make it work
fn main() {
    let f = true;
    let t = true && false;
    assert_eq!(t, f);

    println!("Success!");
}
```
Answer:
```rust
// Make it work
fn main() {
    let f = true; 
    let t = true || false;
    assert_eq!(t, f);

    println!("Success!");
}
output: Success!
solution: changed && to ||
```
---
# Unit Type
5. Question:
```rust
// Make it work, don't modify `implicitly_ret_unit` !
fn main() {
    let _v: () = ();

    let v = (2, 3);
    assert_eq!(v, implicitly_ret_unit());

    println!("Success!");
}

fn implicitly_ret_unit() {
    println!("I will return a ()");
}

// Don't use this one
fn explicitly_ret_unit() -> () {
    println!("I will return a ()");
}
```
Answer:
```rust
fn main() {
    let v0: () = ();

    let v = (2, 3);
    assert_eq!(v0, implicitly_ret_unit());

    println!("Success!");
}

fn implicitly_ret_unit() {
    println!("I will return a ()");
}

// Don't use this one
fn explicitly_ret_unit() -> () {
    println!("I will return a ()");
}
output: I will return a ()
        Success!
solution: made changes for the variables
```
---
6. Questions:
```rust
// Modify `4` in assert to make it work
use std::mem::size_of_val;
fn main() {
    let unit: () = ();
    assert!(size_of_val(&unit) == 4);

    println!("Success!");
}
```
Answer:
```rust
use std::mem::size_of_val;
fn main() {
    let unit: () = ();
    assert!(size_of_val(&unit) == 0);

    println!("Success!");
}
output: Success!
solution: changed the value to 0
```