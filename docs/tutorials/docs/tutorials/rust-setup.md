# Setting up a dev container for Rust
Primary author: Siddhant Borkar (https://github.com/SiddhantBorkar04)

This tutorial will guide you through setting up a DevContainer and creating a basic Rust program. With DevContainers, you don’t need Rust installed on your computer since everything runs in an isolated environment.

## Part 1: Initialization and Setup

### Step 1: Create a Local Directory and Initialize Git
(1) Open your terminal or command prompt.

(2) Create a new directory for your project and navigate to it:
```
mkdir rust-tutorial
cd rust-tutorial
```

(3) Initialize a new Git repository:
```
git init
```

(4) Create a README.md file with a link to this tutorial:
```
echo "# Rust Tutorial" > README.md
echo "Link to tutorial: tutorial link" >> README.md
git add README.md
git commit -m "Initial commit with README"
```

### Step 2: Create a Remote Repository on GitHub
(1) Log in to your GitHub account and create a new repository:
Repository Name: comp423-rust-tutorial
Description: "Hello World in Rust"
Visibility: Public

(2) Do not initialize the repository with a README, .gitignore, or license.

(3) Click Create Repository.

### Step 3: Link Your Local Repository to GitHub
(1) Add the GitHub repository as a remote:
```
git remote add origin https://github.com/<your-username>/comp423-rust-tutorial.git
```
Obviously, make sure to replace <your-username> with your GitHub username.

(2) Rename your default branch to main (if it isn’t already):
```
git branch -M main
```

(3) Push your local commits to GitHub:
```
git push --set-upstream origin main
```

## Part 2: Setting up the DevContainer
### Step 1: Add DevContainer Configuration
(1) Open the rust-tutorial directory in VS Code (File > Open Folder).

(2) Install the Dev Containers extension for VS Code.

(3) Create a .devcontainer directory in your project with the file devcontainer.json:
```
mkdir .devcontainer
```

(4) Add the following configuration to devcontainer.json:
```
{
    "image": "mcr.microsoft.com/devcontainers/rust:0-1",
    "extensions": [
        "rust-lang.rust-analyzer"
    ],
    "settings": {}
}
```

### Step 2: Reopen the Project in a VSCode DevContainer
(1) Press Ctrl+Shift+P (or Cmd+Shift+P on Mac), type "Dev Containers: Reopen in Container," and select it.

(2) Wait for the container to build and set up (this might take a few minutes).

(3) Verify the Rust installation by checking its version in the terminal:
```
rustc --version
```
You should see the installed version of Rust displayed.

## Part 3: Creating Hello World in Rust
### Step 1: Initialize a Rust Project
(1) Use the cargo new command to create a new binary project without initializing another Git repository:
```
cargo new --vcs none .
```

(2) This creates a src/main.rs file with a basic structure and sets up the necessary project files.

### Step 2: Code Hello World
(1) Open the src/main.rs file in VS Code.

(2) Replace its contents with the following code:
```
fn main() {
    println!("Hello COMP423");
}
```

### Step 3: Build and Run Your Program
#### Using cargo run (Build + Execute)
The cargo run command compiles and executes the program in one step, making it ideal for quick testing.

(1) Compile and execute the program in one step with:
```
cargo run
```

(2) This command compiles the source code into a binary and immediately runs it. You should see Hello COMP423 printed in the terminal.

#### Using cargo build (Build Only)
The cargo build command compiles the program without executing it, which is useful when preparing a binary for deployment. This is similar to the gcc command where you compile the code into an a.out file and run it manually.

(1) Compile your program into a standalone binary with:

(2) This creates an executable binary in the target/debug directory

(3) Run the compiled binary directly:
```
./target/debug/rust-tutorial
```

## Part 4: Push to GitHub

(1) Stage and commit your changes:
```
git add .
git commit -m "Hello World Program"
```

(2) Push the changes to your GitHub repository:
```
git push origin main
```

You’ve successfully created and run a basic Rust Hello World program using a DevContainer. Congratulations on completing this tutorial!