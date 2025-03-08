## Chapter 3
### Learnings
#### Variables
1. By default, variables are immutable.
2. You can make them mutable by adding `mut` in front of the variable name. E.g `let mut x=0;`
3. YOu declare constants by the `const` keyword, instead of the `let` keyword, and the type of the value must be annotated.
Constants must be set to constant expressions, not to the result of a function call or any other value that could only be
computed at runtime. Rust's naming convention for constants is to use all uppercase with underscores between words, and underscores can be inserted in literals to improve readability. E.g. ` const MAX_POINTS:u32=100_000;` Constants are valid for the entire time a program runs, within the scope they were declared in.
4. You can declare a new variable with the same name as a previous variable, and the first variable is **shadowed** by the new variable. We can shadow a variable by using the same variable's name and repeating the use of the `let` keyword. Since shadowing is declaring a new variable, we can change the variable type of the new variable despite using the same name.

#### Data Types 
1. Scalar Types
   1. Integer - `i8`, `u8`/ `i16`, `u16`/ `i32`, `u32`/ `i64`, `u64`/`i128`, `u128`/`isize`, `usize`
   2. Floating points - `f32` and `f64`
   3. Boolean -  `bool` which is either `true` or `false`
   4. Character -  `char` literals are specified with single quotes like `'a'` or `'b'`. Rust `char` types are four bytes in size and represents a Unicode Scalar Value, which means it can represent a lot more than just ASCII. Accented letters, Chinese, Japanese, and Korean characters; emoji; and zero-width spaces are all valid `char` values in Rust.
2. Compound Types
    1. Tuples - tuples are groups of values into one type. Tuples have a fixed length, they cannot grow or shrink in size. A tuple is created by writing a comma-separated list of values inside parethesis. Each position in the tuple has a type, and the types don't have to be the same. E.g. ` let tup:(i32, f64, u8)=(500, 6.4, 1);` We use pattern matching to `destructure` a tuple value. E.g `let (x,y,z)=tup;` We could also a tuple element directly by using a period (.) follwed by the index of the value we wanted. E.g `let five_hundred = tup.0;`

    2. Arrays- unlike tuples, arrays in Rust have elements all of the same type; and like Rust tuples, they have fixed lengths. Arrays are useful if you want to allocate your data on the stack rather than on the heap. Rust arrays are written as comma-separated values in side square brackets. An example of when you might want to use an array is when the program needs to know the names of the months of the year.  A vector type, provided by the standard library, is similar to the array but can grow or shrink in size.  E.g. `let months = ["January", "February", "March"...];` You can accesss elements of an array using indexing like `let Jan = months[0]'`

#### Functions 
1. Rust functions use snake_case where all letters are in lowercase, and underscores separate words.
2. Function definitions in Rust start with `fn` and have a set of parenthesis after the function name. The curly braces tell the compiler where the function body begins and ends.
3. In function signatures, you **must** declare the type of each parameter.
4. Function bodies are made up of a series of statements optionally ending in an expression.
5. Expressions do not include semicolons. If you add a semicolon to the end of an expression, you turn it into a statement, which will then not return a value.
6. In Rust, the return value of the function is synonymous with the value of the final expressionin the block of the body of the function. You can return early from a function using the `return` keyword and specifying a value, but most functions return the last expression implicitly.

#### Comments
1. In Rust, comments must start with two slashes and continues until the end of the line. For comments that extend beyond a single line, you'll need to include // on each line.
2. Comments can also be placed at the end of lines containing code.

#### Control Flow
1. If expressions
    1. All If expressions start with the `if` keyword followed by a condition (which has to evaluate to a Boolean. No need for parentheses.)
    2. Since If expressions are expressions, they evaluate to a value. Therefore, you could use an If expresssion on the right side of a `let` statement.
    3. Using too many `else if` expressions can clutter your code, so if you have more than one, you might want to refactor your code. Chapter 6 describes a powerful Rust branching construct called `match` for these cases.

2. Loops - A loop runs through the code inside the loop body to the end then starts immediately back at the beginning.
   1. `loop` 
       - executes a block of code over and over again forever or until you explicitly tell it to stop. 
       - You may place the `break` keyword within the loop to tell the program when to stop executing the loop.
       - One of the uses of a loop is to retry an operation that might fail. However you might need to pass the result of that operation to the rest of your code. You can add the value you want returned after the break expression you used to stop the loop; the value will be returned out of the loop so you can use it.
   2. `while`
       - loops while the condition is true
   3. `for` 
       - used to loop over a collection.

```
        fn main(){
            let a=[10,20,30,40,50];
            for element in a.iter(){
                println!('The value is {}", element);
            }
        } 
```

       - used to loop a certain number of times. The way to do that would be to use a `Range`, which is a type provided by the standard library that generates all numbers in a sequence starting from one number and ending before another number. You can reverse a range be `...(a..b).rev(){}`
```
        for i in (1..5){
            println!("{}!", i);
        }
```
