## Defining Modules to Control Scope and Privacy ##

Modules let us organize code within a create into groups for readability and reuse. Modules also control the _privacy_ of items, which is whether the item can be used by outside code (public) or is internal to an implementation detail and not availalbe for outside use (private).
````
mod front_of_house{
    mod hosting {
        fn add_to_waitlist(){}
        fn seat_at_table(){}
    }
    mod serving{
        fn take_order(){}
        fn serve_order(){}
        fn take_payment(){}
    }
}
````
We define a module by starting with the **mod** keyword and then specify the name of the module. Inside modules, we can have other modules. Modules can also hold definitions for other items such as structs, enums, constants, traits, or---as in the listing above---functions.

If module A is contained inside module B, we say module A is the _child_ of module B and that module B is the _parent_ of module A. The entire module tree is rooted under the implicit module named **crate**.

## Paths for Referring to an Item in the Module Tree ##
To show Rust where to find an item in a module treee, we used a path in the same way we use a path when navigating a filesystem. If we want to call a function, we need to know its path.

A path can take two forms:
- An _absolute path_ starts from a crate by using a crate name or a literal crate. We can use the _crate_ keyword to start an abosolute path. Using the crate name to start from the crate root is like using / to start from the filesystem root in your shell.

- A _relative path_ starts from the current module and uses _self_, _super_, or an identifier in the current module.

Choosing to use a relative or absolute path is a decision you'll make based on your project. The decision should depend on whether you're more likely to move item definition code from or together with the code that uses them.

Both absolute and relative paths are followed by one or more identifiers separated by double colons (::).

Modules aren't useful only for organizing your code. They also define Rust's _privacy boundary_: the line that encapsulates the implementation details external code isn't allowed to know about, call, or rely on. So, if you want to make an item like  a function or struct private, you put it in a module.

The way privacy works in Rust is that **all items** are **private be default**. Items in a parent module can't use items inside a child module, but items in a child module can use private items in their ancestor modules.

But you can expose the inner parts of child modules to outer ancestor modules by using the _pub_ keyword to make an item public.
Making the module public doesn't make its contents public. The _pub_ keyword on a module only lets code in its ancestor modules refere to it.