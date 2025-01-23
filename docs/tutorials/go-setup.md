# Setting Up a Dev Container for Go

* Primary author: [Sanjana Gopalswamy](https://github.com/sgopal08)

* Reviewer: [Caitlin Estrada](https://github.com/caitlinestrada27)


## Prerequisites

Before getting started, ensure you have the following installed on your system:

1. [**Visual Studio Code**](https://code.visualstudio.com/) – A lightweight code editor that supports DevContainers.
2. [**Docker**](https://www.docker.com/products/docker-desktop/) – Required to run the DevContainer.
3. **VS Code Extensions:**
    * Dev Containers (install from VS Code marketplace)
    * Go (Made by the Go Team at Google)

## Step 1: Create a New Project Directory
1. Open the terminal and create a new directory for your project:
```
mkdir comp423-go-tutorial
cd comp423-go-tutorial
```

2. Initialize a new Git repository:
```
git init
```

## Step 2: Add Development Container Configuration
1. Open the `comp423-go-tutorial` directory in VS Code:
    * Go to File > Open Folder and select your project directory.
2. Install the Dev Containers extension:    
    * Open the Extensions Marketplace (Ctrl+Shift+X), search for "Dev Containers," and install it.
3. Create a `.devcontainer` directory in the project root:
```
mkdir .devcontainer
```
!!! tip "Tip: "
    You can also create a new file through VSCode's Explorer panel.

4. Inside the `.devcontainer` directory, create a `devcontainer.json` file with the following content:

```
{
  "name": "COMP423 Go Tutorial",
  "image": "mcr.microsoft.com/devcontainers/go:latest",
  "customizations": {
    "vscode": {
      "extensions": ["golang.go"]
    }
  },
  "postCreateCommand": "go mod init comp423-go-tutorial"
}
```
### Explanation of `devcontainer.json`:

* `name`: Specifies a descriptive name for the DevContainer.

* `image`: Uses Microsoft's official Go DevContainer image.

* `customizations`: Installs the official Go extension for VS Code.

* `postCreateCommand`: Initializes a Go module for dependency management.

## Step 3: Reopen in Dev Container
1. Open the command palette in VS Code (Cmd+Shift+P) and run: **Dev Containers: Reopen in Container**
2. Wait for the container to build and start.

## Step 4: Verify Go Installation
1. Open a terminal inside the container and run:
```
go --version
```
!!! bug "Look Out"
    Make sure it outputs a recent Go version! (i.e. Such as go version ex. Go 1.23)



## Step 5: Create a **Hello COMP423** Program
1. Create a new file `main.go` in the project root with the following content:
```
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```
2. Initialize the Go module:
```
go mod tidy
```

## Step 6: Running and Building the Go Program

1. Run the Go program directly:
```
go run main.go
```
!!! question "Did you know?"
    This command compiles and runs the program in a single step!


2. Build the Go program:

```
go build -o hello_comp423 main.go
```
This generates an executable binary named `hello_comp423`.

```
./hello_comp423
```
3. Unlike go run, the compiled binary does not need the Go environment to execute.

### Explanation of Commands
* `go run`: Compiles and runs the program temporarily without generating an executable file.

* `go build`: Compiles the source code and produces a standalone binary, similar to using gcc for C programs.

**Running the binary:** Executes the compiled program without involving the Go runtime directly.

!!! tip "Success!"
    You have successfully set up a DevContainer for Go, written a "Hello COMP423" program, and learned how to run and build it. You can now continue developing Go applications within a consistent and containerized environment.

## Citations & Resources
[Go Documentation](https://go.dev/doc/)

[COMP423 MkDocs Tutorial](https://comp423-25s.github.io/resources/MkDocs/tutorial/#what-is-a-development-dev-container)