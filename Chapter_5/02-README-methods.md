### Method Syntax ###

Methods are similar to functtions. However methods are different from functtions
in that they are defined within the context of a struct, and their 
**first parameter is always self**  which represents the _instance of the struct_ the method is being called on.

#### Defining Methods ####
````
struct Rectangle{
    width:u32,
    height:u32
}

impl Rectangle {
    fn area(&self) ->u32 {
        self.width * self.height
    }
}

fn main(){
    let rect1 = Rectangle {width:30, height:30};
    println!("The area of the rectangle is {} square pixels.", rect.aread() );
}
````

To define the function within the context of Rectangle, we start an _impl_ (implementation) block. The method syntax goes after an instance; we add a dot followed by the method name, paretheses, and any arguments. Methods can take ownership of _self_, borrow _self_immutably , or borrow _self_ mutably, just as they can any other parameter. If we wanted to change the instance that we've called the method on as part of what the method does, we'd use _&mut self_ as the first parameter.

#### Methods with More Parameters ####
````
impl Rectangle {
    fn area(&self) ->u32 {
        self.width * self.height
    }
    fn can_hold(&self, other:&Rectangle)->book{
        self.width > other.width && self.height > other.height
    }
}
````

#### Associated Functions ####
We're allowed to define functions within the _impl_ blocks that don't take self as a parameter. These are called **associated functions**.  Associated functions are usually used for constructors that will return a new instance of the struct.
````
impl Rectangle{
    fn square(size:u32)->Rectangle{
        Rectangle{width:size, height:size}
    }
}
````
To call this associated function, we use the :: syntax with the struct name; `let sq=Rectangle::square(3);` is an example. This function is name-spaced by the struct: the :: syntax is used for both associated functions and namespaces created by modules. 
#### Multiple impl Blocks ####

Each struct is allowed to have multiple impl blocks. There may be no reason to separate methods into multiple impl blocks, but it is valid syntax.









