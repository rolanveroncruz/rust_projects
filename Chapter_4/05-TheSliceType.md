#### The Slice Type
1. Another data type that does not have ownership is the *slice*. Slices let you reference continguous sequence of elements in a collection rather than the whole collection.

2. Other than the `String` slice discussed below, there are many other slice types, e.g. array slice, that will be discussed later on.


##### The String Slice
1. A string slice is a reference to a part of a `String`, and looks like this:
```
let s = String::from("Hello, World!")

let hello = &s[0..5];
let world = &s[6..11];
```
2. The type that signifies a "string slice" is `&str`.

###### String Literals are string slices
In `let s="Hello, World!"` the type of `s` is `&str`.
String literals are *immutable*.

3. String slices are *immutable references*.



