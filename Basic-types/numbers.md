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
---
4. Question:
```rust
// Fill the blanks to make it work
fn main() {
    assert_eq!(i8::MAX, __); 
    assert_eq!(u8::MAX, __); 

    println!("Success!");
}
```
Answer:
```rust
fn main() {
    assert_eq!(i8::MAX, 127); 
    assert_eq!(u8::MAX, 255); 

    println!("Success!");
}

output: Success!
solution: adding 127 for i8 and 255 for u8 which is the maximum value for the respective variable size
```
---
5. Question:
```rust
// Fix errors and panics to make it work
fn main() {
   let v1 = 251_u8 + 8;
   let v2 = i8::checked_add(251, 8).unwrap();
   println!("{},{}",v1,v2);
}
```
Answer:
```rust
fn main() {
   let v1 = 247_u8 + 8;
   let v2 = i8::checked_add(119, 8).unwrap();
   println!("{},{}",v1,v2);
}

output: 255,127
solution: corrected 251_u8 to 247_u8 in v1 and (251,8) to (119,8) in v2, because it is the max value of u8 and i8.
```
6. Question:
```rust
// Modify `assert!` to make it work
fn main() {
    let v = 1_024 + 0xff + 0o77 + 0b1111_1111;
    assert!(v == 1579);

    println!("Success!");
}

```
Answer:
```rust
fn main() {
    let v = 1_024 + 0xff + 0o77 + 0b1111_1111;
    assert!(v == 1597);

    println!("Success!");
}
output: Success!
solution: corrected (v == 1579) to (v == 1597)
```
---
7. Question:
```rust
fn main() {
    let x = 1_000.000_1; // f64
    let y: f32 = 0.12; // f32
    let z = 0.01_f64; // f64

    println!("Success!");
}
```
Answer:
```rust
output: Success!
solution: write f64 in the comment area for x which is the data type of x
```
---
8. Question:
```rust
// Make it work in two distinct ways
fn main() {
    assert!(0.1+0.2==0.3);

    println!("Success!");
}
```
Answer:
```rust
fn main() {
    assert!(0.1+0.2==0.3);

    println!("Success!");
}
```
```rust
fn main() {
    assert!((0.1_f64+0.2-0.3).abs() < 0.001);

    println!("Success!");
}
```
---
9. Question:
```rust
// Two goals: 1. Modify assert! to make it work 2. Make println! output: 97 - 122
fn main() {
    let mut sum = 0;
    for i in -3..2 {
        sum += i
    }

    assert!(sum == -3);

    for c in 'a'..='z' {
        println!("{}",c);
    }
}
```
```rust
fn main() {
    let mut sum = 0;
    for i in -3..2 {
        sum += i
    }

    assert!(sum == -5);

    for c in 'a'..='z' {
        println!("{}",c as u8);
    }
}
output: 
97
98
99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
solution: added c as u8 because the output will be unsigned integers
```
---
10. Question:
```rust
// Fill the blanks
use std::ops::{Range, RangeInclusive};
fn main() {
    assert_eq!((1..__), Range{ start: 1, end: 5 });
    assert_eq!((1..__), RangeInclusive::new(1, 5));

    println!("Success!");
}
```
Answer:
```rust
use std::ops::{Range, RangeInclusive};
fn main() {
    assert_eq!((1..5), Range{ start: 1, end: 5 });
    assert_eq!((1..=5), RangeInclusive::new(1, 5));

    println!("Success!");
}
output: Success!
```
---
11. Question:
```rust
// Fill the blanks and fix the errors
fn main() {
    // Integer addition
    assert!(1u32 + 2 == __);

    // Integer subtraction
    assert!(1i32 - 2 == __);
    assert!(1u8 - 2 == -1); 
    
    assert!(3 * 50 == __);

    assert!(9.6 / 3.2 == 3.0); // error ! make it work

    assert!(24 % 5 == __);
    // Short-circuiting boolean logic
    assert!(true && false == __);
    assert!(true || false == __);
    assert!(!true == __);

    // Bitwise operations
    println!("0011 AND 0101 is {:04b}", 0b0011u32 & 0b0101);
    println!("0011 OR 0101 is {:04b}", 0b0011u32 | 0b0101);
    println!("0011 XOR 0101 is {:04b}", 0b0011u32 ^ 0b0101);
    println!("1 << 5 is {}", 1u32 << 5);
    println!("0x80 >> 2 is 0x{:x}", 0x80u32 >> 2);
}
```
Answer:
```rust

```