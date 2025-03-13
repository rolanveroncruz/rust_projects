
#### The String Type
1. Other than a string literal which is immutatable, Rust has a second string type, `String`. This type is allocated in the heap and as such is able to store an amount of tezxt that is unknown to us at compile time.  You can create a `String` from a string literal using the `from` function like so:
    
    let mur s=String::from("Hello");
    s.push_str(", world!); // appends a string literal.
    println!("{}", s);   //will print Hello, world!

2. When we assign some `String` s1 to s2, ie. `let s1=String::from("hello"); s2=s1` the `String` data is copied, meaning we copy the pointer, the length, and the capacity that are on the stack. We do not copy the data on the heap that the pointer refers to.
3. Earlier we said when a variable goes out of scope, Rust automatically calls the `drop` function and cleaans up the heap memory for that variable. This could have been a problem: when s2 and s1 go out of scope they will both try to free the same memory. This is known as the `double free` error.
4. Instead of trying to copy the allocated memory, Rust considers s1 to no longer be valid and therefore, Rust doesn't need to free anything when s1 goes out of scope. 
5. Because Rust invalidates the variable, instead of being called a copy, it's known as a `move`.
6. Rust will never automatically create deep copies of your data. Therefore any automatic copying can be assumed to be inexpensive in terms of runtime performance. 