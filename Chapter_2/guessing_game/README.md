## guessing_game

### Learnings
1. `let mut x` declares x as a mutable variable; normally variables are immutable. And in this particular case,
`let mut x = String::new()` allows rust to infer x's type.
2. `String` is a string type provided by the standard library that is a growable, UTF-8 encoded bit of text. `::` in `::new`  indicates that `new` is an *associated function* of the String type. An *associated function* is implemented on a type rather than on an insultance. Some other languages call this a *static method*.
3. `...read_line(&mut guess)` passes a reference to guess that allows read_line to change it. `read_line` writes the input string into `guess`.
4. If we didn't put in `use std::io`, we could have used `std::io.read_line`.
5. `read_line()` returns a value, an `io::Result`. The `Result` type is an enumeration or `enum`. `Result`'s variants are `Ok` and `err`. An instance of `io::Result` has an `expect` method that one can call. If the instance of `Result` has an `err` value, `expect`will cause the program to crash and display the message that you passed as an argument to `expect`; but if `Result` has an `Ok` value, `expect` will return the return value of the function, which in the case of `read_line` is the number of bytes of the input.
6. To use external code / libraries, add them to the `Cargo.toml` file. Like what we did with `rand`, from which we'll use a random number generator. 
7. To convert `guess` from a string to a number, a `u32`, we use `trim()` then `parse()`.
8. To compare we use `x.cmp(y)` to compare x with y. This returns an `std::cmp::Ordering` for which we use a `match` to process.
9. `loop` creates an infinite loop out of which we can `break;` 
10. Instead of using `.expect()` in `...parse()` which can crash the program if conversion can't be done, we use `match` to process the result, which is either `Ok`, where we just return the number; or `Err`, where we can handle the error, which in this case, we choose to ignore, and just `continue` at the top of the `loop`.