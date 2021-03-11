## String Interning made super simple and performant

```rust
let mut db = StringInterning::with_capacity(100000);

// you can also do
// let db = StringInterning::new();

for i in 0..5000000 {
    db.add(i.to_string());
}

for i in 0..5000000 {
    let a = i.to_string();
    assert_eq!(db.add(&a).0, i);
    assert_eq!(db.get(StringId(i)), a);
}

for i in 0..5000000 {
    let a = i.to_string();
    assert_eq!(db.get(StringId(i)), a);
}

```

I created this for a personal project that I just had too much string cloning.

## What is string interning?
Just a way of keeping a single copy of a string in memory,
if you add a new string in the data structure it will be allocated,
but when you try to add it again it won't be allocated and return the same id,
if you give that id to the data structure it will return the reference of the string.
