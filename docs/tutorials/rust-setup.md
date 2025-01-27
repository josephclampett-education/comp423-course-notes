# Hello World Tutorial for Rust Using Container
* Primary author: [Joseph Clampett](https://github.com/josephclampett-education)
* Reviewer: [Simon Felt](https://github.com/simofel)

### Prerequisites
1. [**Git**](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git)
2. [**Visual Studio Code**](https://code.visualstudio.com/)
3. [**Docker**](https://www.docker.com/products/docker-desktop/)


### Creating repository
- Open your terminal and create a new directory for the project:
```
mkdir {directory name}
```

- Then enter it:
```
cd {directory name}
```

- Finally, initialize the folder as a new git repository: 
```
git init
```

- After this, close the terminal and open the folder in VS Code using:
> File > Open Folder

### Initializing Docker

Once the folder is open in VS code, we are ready to create our container.

- First, install the Dev Container extension (`ms-vscode-remote.remote-containers`) from the Extensions tab in VS Code.

- Then, in the Explorer tab, use the new folder and file icons to create the following file:
> .devcontainer/devcontainer.json
```json
{
	"name": "Rust Hello World",
	"image": "mcr.microsoft.com/devcontainers/rust:latest",
	"customizations": {
	  "vscode": {
		"settings": {},
		"extensions": ["rust-lang.rust-analyzer"]
	  }
	},
	"postCreateCommand": "rustc --version"
}
```

- Finally, press [Ctrl/Cmd] + [Shift] + [P] and choose "Dev Containers: Reopen in Container." VS Code will begin downloading the container package if it is not already installed.

### Creating Rust project

Once VS Code reloads in the container, note the Rust version in the automatic setup terminal. This terminal will ask you to close it once setup tasks have been completed, so you will need a new terminal. If one is already open in the Terminal tab, use it, otherwise go to the top menu bar and create a new Terminal using Terminal > New Terminal.

- Create a new project using
```
cargo new hello-world --vcs none
```

- Navigate into the new project folder using
```
cd hello-world
```

- Then run the project using
```
cargo run
```

- Confirm the output is 
> Hello, world!

- Finally, make a change by opening the `hello-world/src/main.rs` file and changing the code to
```rust
fn main() {
    println!("Hello, world (new)!");
}
```

- If you would like to rebuild without automatically running the compiled executable, you can use
```
cargo build
```
Cargo build is conceptually similar to using gcc to compile C and C++, in this case it takes .rs files and compiles + links them into the same type of executable as gcc and its linker create.

- You can re-run the program using
```
cargo run
```
- Note that no compilation was performed because the `build` command already compiled the latest changes.