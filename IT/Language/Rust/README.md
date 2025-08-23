# Rust

## Ownership

Ownership is a set of rules that govern how a Rust program manages memory:

1. Each value in Rust has an owner.
2. There can only be one owner at a time.
3. When the owner goes out of scope, the value will be dropped.

```rust
{
    let s = String::from("hello"); // s has ownership
    // do stuff with s
} // this scope is now over, and s will be dropped
{
    let s1 = String::from("hello"); // s1 has ownership
    let s2 = s1; // ownership is moved to s2, so s1 cannot be used anymore
    let s3 = s2.clone(); // s2 is cloned, which gets the ownership of new data
} // s2 and s3 are dropped
{
    let x = 114514;
    let y = x; // copy
    // both x and y can be used
}
```

Rust has a special annotation called the `Copy` trait. If a type implements the `Copy` trait, old value is still valid after assignment, because it is copied instead of moved.

Rust won't let a type implement both `Copy` and `Drop` traits.

Here are some of the types that implement `Copy` trait:

* All integer types, such as `i32`.
* The Boolean type, `bool`, with values `true` and `false`.
* All the floating-point types, such as `f64`.
* The character type, `char`.
* Tuples, if they only contain types that also implement `Copy`. For example, `(i32, i32)` implements `Copy`, but `(i32, String)` does not.
