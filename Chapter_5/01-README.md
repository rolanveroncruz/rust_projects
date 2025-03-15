
### Using Field Init Shorthand When Variables and Fields Have the Same Name

Because the parameter names and the struct field names are exactly the same name, we can use the *field init shorthand* syntax to rewrite build_user so that it behaves exactly the same but doesn't have the repetiion of email and username:

````
fn build_user(email:String, username:String)-> User{
    User{
        email,
        username,
        active: true
        sign_in_count:1,
    }
}
````

### Creating Instances from Other Instances with Struct Update Syntax
It is often useful to create a new instance of a struct tht uses most of an old instance's values but change some. YOu'll do this with the struct update syntax:
````
    let user1 = User{
        email: String:;from("another@exaple.com"),
        username: String::from("anotherusername456"),
        active: true,
        sign_in_count:1,
    }
    let user2 = User{
        email: String:;from("stillanother@exaple.com"),
        username: String::from("stillanotherusername456"),
        ..user1
    }
````

The ... syntax specifies that the remaining fields not explicitly set should have the same values as the fields in the given instance.
**Check if the unspecified fields are moved or copied.**

### Using Tuple Structs Without Named Fields to Create Different Types

You can also define structs that look similar to tuples, called *tuple structs*. Tuple structs have the added meaning the struct name provides but don't have names associated with their fields: rather they just have the types of the fields. Tuple structs are useful when you want to give the whole tuple a name, and make the tuple a different type from the other tuples, and naming each field (as in a regular struct) would be verbose or redundant.
````
struct Color(i32, i32, i32);
struct Point(i32, i32, i33);
let black = Color(0,0,0);
let origin = Point(0,0,0);
````

Note that black and origin values are different types. Each struct you define is its own type, even though the fields within the struct have the same type. Functions that take a parameter of type Color cannot take a Point.

### Unit-Like Structs Without Any Fields
You can also define a struct with no fields! These are called *unit-like structs* because they behave similarly to (), the *unit type*.
