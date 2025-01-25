# Setting up a dev container for Rust

* Primary author: [Falisha Khokhar](https://github.com/falishakhokhar)
* Reviewer: [Lucille Moore](https://github.com/lmoore36)

Welcome! In this tutorial, you'll learn how to set up a basic Rust Development Container in VS Code and initialize and configure a GitHub repository with a simple hello world example.

!!! note
    Parts One and Two of this tutorial are adapted from Kris Jordan's [Starting a Static Website Project with MkDocs](https://comp423-25s.github.io/resources/MkDocs/tutorial/) tutorial, with modifications to support Rust development. Thanks, Kris!

## Prerequisites

Before we dive in, make sure you have:

1. A GitHub account: If you don’t have one yet, sign up at [GitHub](https://github.com/).
2. Git installed: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don’t already have it.
3. Visual Studio Code (VS Code): Download and install it from [here](https://code.visualstudio.com/).
4. Docker installed: Required to run the dev container. [Get Docker here](https://www.docker.com/products/docker-desktop).
5. Command-line basics: Your COMP211 command-line knowledge will serve you well here. If in doubt, review the Learn a CLI text!

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

```
echo "# Rust Starter Project" > README.md
git add README.md
git commit -m "Initial commit with README"
```

## Part 2. Setting Up the Development Environment

### Step 1. Add Development Container Configuration
### Step 2. Reopen the Project in a VSCode Dev Container

## Part 3. Getting Started with Rust

### Step 1. Create a Binary Project
### Step 2. Write the "Hello COMP423" Program
### Step 3. Compile and Run your Program with build