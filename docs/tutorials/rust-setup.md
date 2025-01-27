# Setting up a dev container for Rust
* Primary author: [Falisha Khokhar](https://github.com/falishakhokhar)
* Reviewer: [Lucille Moore](https://github.com/lmoore36)

## Introduction

Welcome! In this tutorial you'll learn how to set up a basic Rust Development Container in VS Code and initialize and configure a GitHub repository with a simple hello world example.

!!! note
    Parts One and Two of this tutorial are adapted from Kris Jordan's [Starting a Static Website Project with MkDocs](https://comp423-25s.github.io/resources/MkDocs/tutorial/) tutorial, with modifications to support Rust development.

## Prerequisites

Before we dive in, make sure you have:

1. **Git installed:** [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don’t already have it.
2. **Visual Studio Code (VS Code):** Download and install it from [here](https://code.visualstudio.com/).
3. **Docker installed:** Required to run the dev container. [Get Docker here](https://www.docker.com/products/docker-desktop).
4. **Command-line basics:** Your COMP211 command-line knowledge will serve you well here. If in doubt, review the Learn a CLI text!

## Part 1: Creating a Local Directory and Initializing Git

1. Open your terminal or command prompt.

2. Create a new directory for your project. (Note: Of course, if you'd like to organize this tutorial somewhere else on your machine, go ahead and change into that parent directory first. By default this will be in your user's home directory.):

    ```
    mkdir rust-tutorial
    cd rust-tutorial
    ```

3. Initialize a new Git repository:

    ```
    git init
    ```

4. Create a README file:

    ```markdown
    echo "# Rust Starter Project" > README.md
    git add README.md
    git commit -m "Initial commit with README"
    ```

## Part 2: Setting Up the Development Environment

### Step 1: Add Development Container Configuration

1. In VS Code, open the `rust-tutorial` directory. You can do this via: File > Open Folder.
2. Install the **Dev Containers** extension for VS Code.
3. Create a `.devcontainer` directory in the root of your project with the following file inside of this "hidden" configuration directory: `.devcontainer/devcontainer.json`
4. Update your `devcontainer.json` file to contain the following content:

    ```json
    {
        "name": "Rust Development Environment",
        "image": "mcr.microsoft.com/devcontainers/rust:latest",
        "customizations": {
            "vscode": {
                "extensions":["rust-lang.rust-analyzer"]
            }
        },
        "postCreateCommand": "rustc --version"
    }
    ```

The devcontainer.json file defines the configuration for your development environment. Here, we're specifying the following:

- `name`: A descriptive name for your dev container.
- `image`: The Docker image to use, in this case, the latest version of a Rust environment. 
- `customizations`: Adds useful configurations to VS Code, like installing the rust-analyzer extension. When you search for VSCode extensions on the marketplace, you will find the string identifier of each extension in its sidebar. Adding extensions here ensures other developers on your project have them installed in their dev containers automatically.
- `postCreateCommand`: A command to run after the container is created. In this case, this command ensures Rust is available within the dev container and gives the user a confirmation message about their Rust installation.


### Step 2: Reopen the Project in a VSCode Dev Container

Reopen the project in the container by pressing `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed.

## Part 3: Getting Started with Rust

### Step 1: Create a Binary Project

To create a new package with Cargo, Rust's build system and package manager, run the following command inside the terminal in your Dev Container:

```
cargo new rust-tutorial --vcs none
```

!!! info
    Cargo new initializes a new git repository by default. The `--vcs none` flag indicates that the package manager should not create a new git repository automatically on your behalf.

Your new `rust-tutorial` directory will then have the following structure:

```
cd rust-tutorial
tree .

├── Cargo.toml
└── src
    └── main.rs

1 directory, 2 files
```

`Cargo.toml` is called a manifest, and it contains all of the metadata that Cargo needs to compile your package.

### Step 2: Write the "Hello COMP423" Program

The `src/main.rs` file will automatically generate the following code snippet for you.

```rust
fn main() {
    println!("Hello, world!");
}
```

Update the code to print "Hello COMP423".

### Step 3: Compile and Run your Program

The `cargo build` command compiles the current package and creates an executable file in the `target/debug/` directory. 
```
cargo build
```

To run your executable `rust-tutorial` file, enter the following command in your terminal:
```
./target/debug/rust-tutorial

Hello COMP423
```

!!! info
    If this workflow seems familiar, that's because `cargo build` is similar to COMP211's `gcc` command, in that they both compile source code into an executable. However, `cargo build` places the executable in `target/debug`, while `gcc` creates the output in the current directory (or as specified by -o). Note that neither of these commands run the executable.

Use the `cargo run` command to build and execute the program in one step, without the use of `build`.

```
cargo run

Hello COMP423
```

## Conclusion

Congratulations! You now have a basic dev container set up for a Rust program.