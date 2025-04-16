# Chapter 7 Managing Growing Projects with Packages, Crates, and Modules

## Packages and Crates
- A **crate** is a binary or a library.
- The _crate root_  is a source file that the Rust compiler starts from and makes up the root module of the crate.
- A **package** is one or more crates that provide a set of functionality. It contains a _Cargo.toml_ file that describes how to build those crates.
- A _package_ must contain **zero or more** library crates. And it can contain as many binary crates as you'd like, but it must contain at least one crate (either library or binary).
- When we use the `cargo new` command, Cargo creates a _Cargo.toml_ file, giving us a package.  Cargo follows the convention that `src/main.rs` is the crate root of a binary crat with the same name as the package. Likewise, Cargo knows that if the pakage directory contains a `src/lib.rs`, the package contains a library crate with the same name as the package,   and `src/lib.rs` is its crate root.
- If we have a package that contains `src/main.rs` and `src/lib.rs`, it has two crates: a library and a binary, both with the same name as the package. A package can have multiple binary crates by placinf files in the `src/bin/` directory:each file will be a separate binary crate. 