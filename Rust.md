## Why?

For fun and performance.

## No Seriously Why?

- No exceptions
  - No undefined behavior
- Abstractions over types
- Absurd performance

## The Example

My [personal website](https://whynot.sh/) written in rust load tested (for an hour) at 2,180 requests a second with a
p50 of 35ms and a p95 of 50ms.

This was done with two t4g.medium machines (one web and one db) using about 2.5 cores between the two machines.

Across the nearly 8,000,000 requests there were 264 errors (due to a mistake in sql connection limit settings).

## Important CompSci Concepts

- Function Parameters
  - Pass by value
  - Pass by reference
- Memory Management
  - Stack
  - Heap

## Bad C++ Code

```cpp
Free::Free() {
    this->str = new std::string("hi");
}
Free::~Free() {
    delete this->str;
}

void pass(Free f) {
    // do something with f
}

int main(void) {
    Free f;
    pass(f);
}
```

## The Borrow Checker

It prevents you from doing nonsense with memory. Specifically it cares about all pointers and any non-pointers with data
on the heap.

Example...

```rust
fn print(s: String) {
    println!("{}", s);
}

fn main() {
    let a = "hi".to_string();
    print(a);
    // a cannot be access anymore
}
```

## Another Example

This one works since `i32` implements the `Copy` trait.

```rust
fn print(s: i32) {
    println!("{}", s);
}

fn main() {
    let a: i32 = 12;
    print(a);
    print(a);
}
```

## Fin

Let's get to the [code](https://github.com/whynotavailable/blag).
