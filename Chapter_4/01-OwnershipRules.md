
#### Ownership Rules
1. Each value in Rust has a variable called its *owner*.
2. There can only be one owner at a time.
3. When the owner goes out of scope, the value will be dropped.
    1. A variable is said to be valid from the point it is declared
    2. until the end of the current *scope*.
4. When a vaariable goes out of scope, Rust calls a special function for us. This function is called `drop` and it's where th author of `String` can put the code back into memory. Rust calls `drop` automatically at the closing curly braces (when the `String` goes out of scope.)
