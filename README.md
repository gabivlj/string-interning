## String Interning made super simple and performant

```rs
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