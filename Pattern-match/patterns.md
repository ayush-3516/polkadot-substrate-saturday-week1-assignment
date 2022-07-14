1. Question:
```rust
fn main() {}
fn match_number(n: i32) {
    match n {
        // Match a single value
        1 => println!("One!"),
        // Fill in the blank with `|`, DON'T use `..` or `..=`
        __ => println!("match 2 -> 5"),
        // Match an inclusive range
        6..=10 => {
            println!("match 6 -> 10")
        },
        _ => {
            println!("match 11 -> +infinite")
        }
    }
}
```
Answer:
```rust
fn main() {}
fn match_number(n: i32) {
    match n {
        1 => println!("One!"),
        2 | 3 | 4 | 5 => println!("match 2 -> 5"),
        6..=10 => {
            println!("match 6 -> 10")
        },
        _ => {
            println!("match 11 -> +infinite")
        }
    }
}
```
---
2. Question:
```rust
struct Point {
    x: i32,
    y: i32,
}

fn main() {
    // Fill in the blank to let p match the second arm
    let p = Point { x: __, y: __ };

    match p {
        Point { x, y: 0 } => println!("On the x axis at {}", x),
        // Second arm
        Point { x: 0..=5, y: y@ (10 | 20 | 30) } => println!("On the y axis at {}", y),
        Point { x, y } => println!("On neither axis: ({}, {})", x, y),
    }
}
```
Answer:
```rust
struct Point {
    x: i32,
    y: i32,
}
fn main() {
    let p = Point { x: 2, y: 20 };
    match p {
        Point { x, y: 0 } => println!("On the x axis at {}", x),
        Point { x: 0..=5, y: y@ (10 | 20 | 30) } => println!("On the y axis at {}", y),
        Point { x, y } => println!("On neither axis: ({}, {})", x, y),
    }
}
```
---
3. Question:
```rust
// Fix the errors
enum Message {
    Hello { id: i32 },
}

fn main() {
    let msg = Message::Hello { id: 5 };

    match msg {
        Message::Hello {
            id:  3..=7,
        } => println!("Found an id in range [3, 7]: {}", id),
        Message::Hello { id: newid@10 | 11 | 12 } => {
            println!("Found an id in another range [10, 12]: {}", newid)
        }
        Message::Hello { id } => println!("Found some other id: {}", id),
    }
}
```
Answer:
```rust
enum Message {
    Hello { id: i32 },
}
fn main() {
    let msg = Message::Hello { id: 5 };
    match msg {
        Message::Hello {
            id:  id@3..=7,
        } => println!("Found an id in range [3, 7]: {}", id),
        Message::Hello { id: newid@(10 | 11 | 12) } => {
            println!("Found an id in another range [10, 12]: {}", newid)
        }
        Message::Hello { id } => println!("Found some other id: {}", id),
    }
}
```
---
4. Question:
```rust
// Fill in the blank to make the code work, `split` MUST be used
fn main() {
    let num = Some(4);
    let split = 5;
    match num {
        Some(x) __ => assert!(x < split),
        Some(x) => assert!(x >= split),
        None => (),
    }

    println!("Success!");
}
```
Answer:
```rust
fn main() {
    let num = Some(4);
    let split = 5;
    match num {
        Some(x) if x < split => assert!(x < split),
        Some(x) => assert!(x >= split),
        None => (),
    }
    println!("Success!");
}
```
---
5. Question:
```rust
// Fill the blank to make the code work
fn main() {
    let numbers = (2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048);

    match numbers {
        __ => {
           assert_eq!(first, 2);
           assert_eq!(last, 2048);
        }
    }

    println!("Success!");
}
```
Answer:
```rust
fn main() {
    let numbers = (2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048);
    match numbers {
        (first,..,last) => {
           assert_eq!(first, 2);
           assert_eq!(last, 2048);
        }
    }
    println!("Success!");
}
```
---
6. Question:
```rust
// FIX the error with least changing
// DON'T remove any code line
fn main() {
    let mut v = String::from("hello,");
    let r = &mut v;

    match r {
       &mut value => value.push_str(" world!") 
    }
}
```
Answer:
```rust
fn main() {
    let mut v = String::from("hello,");
    let r = &mut v;
    match r {
       value => value.push_str(" world!") 
    }
}
```
---