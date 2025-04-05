### The Option Enum and Its Advantages over Null Values ###

The Option type is used in many places because it encodes the very common scenario in which a value could be something or it could be nothing. Expressing this concept in terms of the type system means the compiler can check whether you've handled all the cases you should be handling: this functionality can prevent bugs that are extremely common in other programming languages.

Rust does not have null, but it does have an enum that can encode the concept of a value being present or abseent. This enum is _Option<T>_, and is defined by the standard library as follows:
````
enum Option<T>{
    Some<T>,
    None,
}
````