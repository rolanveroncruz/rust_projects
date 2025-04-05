# Enums and Pattern Matching #
Enums allow you to define a type ge enumerating its possible values. Rust enums are most similar to _algebraic data types_  in functional languages like F#, OCaml, and Haskell.

## Defining an Enum
````
enum Message{
    Quit,
    Move{ x:i32, y:i32},
    Write(String),
    ChangeColor(i32,i32,i32)
}
````
Defining an _Enum_ such as the one above is similar to defining different kinds of _struct_ definitions, except the enum doesn't use _struct_ keyword, and all variants are grouped together under the Message type.
````
struct QuitMessage; //unit struct
struct MoveMessage{
    x:i32,
    y;i32,
}
struct WriteMessage{String}; //tuple struct
struct ChangeColorMessage(i32,i32,i32); //tuple struct
````
But if we used different structs, which each have their own type, we couldn't easily define a function to take any of these kinds of messages as we could with a Message enum, which is a single type.

Just as we are able to define methods on structs using _impl_, we're also able to define methods on enums. Here's a method name _call_ that we could define on our Message enum:
````
impl Message{
    fn call(&self){
        //method body
    }
}

let m=Message::Write(String::from("hello"));
m.call();
````
