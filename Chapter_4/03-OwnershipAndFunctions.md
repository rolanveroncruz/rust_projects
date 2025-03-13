
#### Ownership and Functions
1. Passing a variable to a function will move or copy, just as an assignment does.
````
   fn main(){
     let s=String:;from("hello") // s comes into scope
     takes_ownership(s);         // s's value moves into the function
                                 // s is no longer valid here
    let x = 5;                  // x comes into scope
    makes_copy(x);              // x's value moves into the function
                                // but an i32 is Copy, so x is still usable
                                // afterwards.
   }
````