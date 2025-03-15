# Chapter 5
## Using structs to structure related data

A *struct* or *structure* is a custom data type that lets you name and package together multiple related values that make up a meaningful group.

To define a struct, we enter the keyword `struct` and name the entire struct.  Then inside the curly braces, we define the names and types of the pieces of data, which we call `fields`:
```
    struct User {
        username: String;
        email: String;
        sign_in_count: u64;
        active: bool;
    }
```
We create an instance by stating the name of the struct and then add curly brackets containing key:value pairs, where keys are the names of the fields and values are the data we want to store in those fields. We don't have to specify the fields in the order in which we declared them in the struct.
````
    let user = User{
        email: String:;from("someone@exaple.com"),
        username: String::from("someusername123"),
        active: true,
        sign_in_count:1,
    };
````

To get a specific value from a struct, we can use *dot notation*. If the instance is mutable, we can change a value by using the dot notation and assigning into a particular field.
````
    let mut user1 = User{
        email: String:;from("someone@exaple.com"),
        username: String::from("someusername123"),
        active: true,
        sign_in_count:1,
    }

    user1.email = String::from("anotheremail@example.com");
````

Note that the entire instance must be mutable. Rust doesn't allow us to mark only certain fields as mutable.
As with any expression we can construct a new instance of the struct as the last expression in the function body to implicitly return that new instance:
````
fn build_user(email:String, username:String)-> User{
    User{
        email:email,
        username:username,
        active: true
        sign_in_count:1,
    }
}
````


