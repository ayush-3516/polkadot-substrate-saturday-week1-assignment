1. Question:
```rust
// Fill in the blanks
fn main() {
    let n = 5;

    if n < 0 {
        println!("{} is negative", n);
    } __ n > 0 {
        println!("{} is positive", n);
    } __ {
        println!("{} is zero", n);
    }
} 
```
Answer:
```rust
fn main() {
    let n = 5;

    if n < 0 {
        println!("{} is negative", n);
    } else if n > 0 {
        println!("{} is positive", n);
    } else {
        println!("{} is zero", n);
    }
    println!("Success!");
} 
```
---
2. Question:
```rust
// Fix the errors
fn main() {
    let n = 5;

    let big_n =
        if n < 10 && n > -10 {
            println!(", and is a small number, increase ten-fold");

            10 * n
        } else {
            println!(", and is a big number, halve the number");

            n / 2.0 ;
        }

    println!("{} -> {}", n, big_n);
} 
```
Answer:
```rust
fn main() {
    let n = 5;
    let big_n =
        if n < 10 && n > -10 {
            println!(", and is a small number, increase ten-fold");
            10 * n
        } else {
            println!(", and is a big number, halve the number");
            n / 2
        };
    println!("{} -> {}", n, big_n);
    println!("Success!");
} 
```
---
3. Question:
```rust
fn main() {
    for n in 1..=100 { // modify this line to make the code work
        if n == 100 {
            panic!("NEVER LET THIS RUN")
        }
    }

    println!("Success!");
} 
```
Answer:
```rust
fn main() {
    for n in 1..100 {
        if n == 100 {
            panic!("NEVER LET THIS RUN")
        }
    }
    println!("Success!");
} 
```
---
4. Question:
```rust
// Fix the errors without adding or removing lines
fn main() {
    let names = [String::from("liming"),String::from("hanmeimei")];
    for name in names {
        // Do something with name...
    }

    println!("{:?}", names);

    let numbers = [1, 2, 3];
    // The elements in numbers are Copy，so there is no move here
    for n in numbers {
        // Do something with name...
    }
    
    println!("{:?}", numbers);
} 
```
Answer:
```rust
fn main() {
    let names = [String::from("liming"), String::from("hanmeimei")];
    for name in &names {    }
    println!("{:?}", names);
    let numbers = [1, 2, 3];
    for n in numbers {    }
    println!("{:?}", numbers);
    println!("Success!");
} 
```
---
5. Question:
```rust
fn main() {
    let a = [4, 3, 2, 1];
    for (i,v) in a.__ {
        println!("The {}th element is {}",i+1,v);
    }
    println!("Success!");
}
```
Answer:
```rust
fn main() {
    let a = [4, 3, 2, 1];
    for (i, v) in a.iter().enumerate() {
        println!("The {}th element is {}", i + 1, v);
    }
    println!("Success!");
}
```
---
6. Question:
```rust
// Fill in the blanks to make the last println! work !
fn main() {
    // A counter variable
    let mut n = 1;

    // Loop while the condition is true
    while n __ 10 {
        if n % 15 == 0 {
            println!("fizzbuzz");
        } else if n % 3 == 0 {
            println!("fizz");
        } else if n % 5 == 0 {
            println!("buzz");
        } else {
            println!("{}", n);
        }


        __;
    }

    println!("n reached {}, so loop is over",n);
}
```
Answer:
```rust
fn main() {
    let mut n = 1;
    while n < 10 {
        if n % 15 == 0 {
            println!("fizzbuzz");
        } else if n % 3 == 0 {
            println!("fizz");
        } else if n % 5 == 0 {
            println!("buzz");
        } else {
            println!("{}", n);
        }
        n += 1;
    }
    println!("n reached {}, soloop is over", n);
    println!("Success!");
}
```
---
7. Question:
```rust
// Fill in the blank
fn main() {
    let mut n = 0;
    for i in 0..=100 {
       if n == 66 {
           __
       }
       n += 1;
    }

    assert_eq!(n, 66);

    println!("Success!");
}
```
Answer:
```rust
fn main() {
    let mut n = 0;
    for i in 0..=100 {
        if n == 66 {
            break;
        }
        n += 1;
    }
    assert_eq!(n, 66);
    println!("Success!");
}
```
---
8. Question:
```rust
// Fill in the blanks
fn main() {
    let mut n = 0;
    for i in 0..=100 {
       if n != 66 {
           n+=1;
           __;
       }
       
       __
    }

    assert_eq!(n, 66);

    println!("Success!");
}
```
Answer:
```rust
fn main() {
    let mut n = 0;
    for i in 0..=100 {
        if n != 66 {
            n += 1;
            continue;
        }
        break;
    }
    assert_eq!(n, 66);
    println!("Success!");
}
```
---
9. Question:
```rust
// Fill in the blanks
fn main() {
    let mut count = 0u32;

    println!("Let's count until infinity!");

    // Infinite loop
    loop {
        count += 1;

        if count == 3 {
            println!("three");

            // Skip the rest of this iteration
            __;
        }

        println!("{}", count);

        if count == 5 {
            println!("OK, that's enough");

            __;
        }
    }

    assert_eq!(count, 5);

    println!("Success!");
}
```
Answer:
```rust
fn main() {
    let mut count = 0u32;
    println!("Let's count until infinity!");
    loop {
        count += 1;
        if count == 3 {
            println!("three");
            continue;
        }
        println!("{}", count);
        if count == 5 {
            println!("OK, that's enough");

            break;
        }
    }
    assert_eq!(count, 5);
    println!("Success!");
}
```
---
10. Question:
```rust
// Fill in the blank
fn main() {
    let mut counter = 0;

    let result = loop {
        counter += 1;

        if counter == 10 {
            __;
        }
    };

    assert_eq!(result, 20);

    println!("Success!");
}
```
Answer:
```rust
fn main() {
    let mut counter = 0;
    let result = loop {
        counter += 1;
        if counter == 10 {
            break counter * 2;
        }
    };
    assert_eq!(result, 20);
    println!("Success!");
}
```
---
11. Question:
```rust
// Fill in the blank
fn main() {
    let mut count = 0;
    'outer: loop {
        'inner1: loop {
            if count >= 20 {
                // This would break only the inner1 loop
                break 'inner1; // `break` is also works.
            }
            count += 2;
        }

        count += 5;

        'inner2: loop {
            if count >= 30 {
                // This breaks the outer loop
                break 'outer;
            }

            // This will continue the outer loop
            continue 'outer;
        }
    }

    assert!(count == __);

    println!("Success!");
}
```
Answer:
```rust
fn main() {
    let mut count = 0;
    'outer: loop {
        'inner1: loop {
            if count >= 20 {
                break 'inner1;
            }
            count += 2;
        }
        count += 5;
        'inner2: loop {
            if count >= 30 {
                break 'outer;
            }
            continue 'outer;
        }
    }
    assert!(count == 30);
    println!("Success");
}
```
---