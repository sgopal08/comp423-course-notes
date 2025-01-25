# Setting Up a Dev Container for Rust

* Primary author: [Caitlin Estrada](https://github.com/caitlinestrada27)
* Reviewer: [Sanjana Gopalswamy](https://github.com/sgopal08)

### Prerequisites
* [**Visual Studio Code**](https://code.visualstudio.com/) with the Microsoft Dev Containers extension
* [**Docker**](https://www.docker.com/products/docker-desktop/) installed for creating and managing containers

### Step 1: Create a new Dev Container project
1. Create a `.devcontainer` directory in the root of your project with the following file inside of this "hidden" configuration directory: `.devcontainer/devcontainer.json`

### Step 2: Create Blank Git Repository and Initialize 
1. Open the terminal and create a new directory for your project: 
```
mkdir comp423-rust-tutorial
cd comp423-rust-tutorial
```

2. Initialize a new Git repository:
```
git init
```

### Step 3: Dev Container Configuration 
The `devcontainer.json` file defines the configuration for your development environment. Here, we're specifying the following: 


* **name**: A descriptive name for your dev container 
* **image**: A base image from Microsoft 
* **extensions**: Add the `rust-analyzer` VSCode plugin by the Rust Programming Language Group
* **version**: Show the `rustc --version` to prove a recent version of Rust

```
// A sample devcontainer.json
{
  "name": "Rust Development",
  "image": "mcr.microsoft.com/vscode/devcontainers/rust:1",
  "extensions": ["matklad.rust-analyzer"],
  "postCreateCommand": "rustup update && rustc --version"
}
```

### Step 4: Create a new rust project
1. Open a new terminal
2. Create a new project using Cargo: 
```
cargo new my_rust_project 
```
3. Navigate into your project directory: 
```
cd my_rust_project
```

### Step 5: Write a basic "Hello COMP 423" program
```rust
// A simple Rust code block to print "Hello, COMP423!"
fn main() {
    println!("Hello, COMP423!");
}
```

### Step 6: Compile
Build your project using Cargo: 
``` 
cargo build
```
!!! question "What does this command do?"
    It compiles your project's source code into an executable binary (if it's a binary project) or a library (if it's a library project).


### Step 7: Run 
Run the project using Cargo:
```
cargo run
```

### Expected Output
```
Hello COMP423!
```
!!! bug
    Verify that this is your output to ensure you followed the tutorial correctly!

## Citations & Resources
[Cargo Documentation](https://doc.rust-lang.org/cargo/guide/creating-a-new-project.html)

[Rust Documentation](https://www.rust-lang.org/learn)

[COMP423 MkDocs Tutorial](https://comp423-25s.github.io/resources/MkDocs/tutorial/#what-is-a-development-dev-container)