# Minishell - 42 Project

## 🚀 Project Overview

**Minishell** is a project at 42 that involves creating a custom shell program in **C**. The goal is to implement a functional shell that can handle basic command execution, redirection, piping, and environment variable management, while parsing input efficiently. A key part of this project is building an Abstract Syntax Tree (AST) to parse the user input before processing it.

### Bonus Features
In addition to basic shell functionalities, I implemented the following bonus features:

- **Wildcards (Globbing)**: Supports the use of wildcards like `*` and `?` in filenames for pattern matching.
- **Command Grouping with Parentheses (`()`)**: Allows commands to be grouped and executed within a subshell.
- **Input Parsing with an Abstract Syntax Tree (AST)**: Instead of directly processing the input, the shell constructs an AST, which simplifies command handling, operator precedence, and redirection.

---

## 💡 Key Features & Bonus Implementations

### Basic Shell Functionality

- **Command Execution**: Reads user input, parses it, and executes commands accordingly.
- **Pipes**: Supports piping between commands using `|` to pass the output of one command as input to another.
- **Redirections**: Handles redirection operators (`>`, `>>`, `<`) for both input and output redirection.
- **Environment Variables**: Supports environment variable management, including setting, unsetting, and displaying them.
- **Built-in Commands**: Handles built-in commands like `cd`, `echo`, `pwd`, `env`, `export`, `unset`, and `exit`.

### 📜 Bonus Features

1. **Wildcards (Globbing)**:
   - The shell supports the use of wildcards like `*`, `?` in commands, enabling file pattern matching. For example:
     - `*.txt` matches all `.txt` files.
     - `file?.txt` matches files like `file1.txt`, `file2.txt`, etc.
   
2. **Command Grouping with Parentheses (`()`):**
   - Commands enclosed in parentheses are grouped and executed in a subshell. This allows users to run multiple commands in a single line, with the grouping affecting only the execution context inside the parentheses.
   - Example: `(cd /home; ls)` will first `cd` into `/home` and then execute `ls` in the same command.

3. **Input Parsing with Abstract Syntax Tree (AST)**:
   - The shell builds an Abstract Syntax Tree (AST) from the user input. The AST represents the structure of the command line input, allowing the shell to handle operators, redirections, and parentheses correctly.
   - Parsing the input into an AST simplifies the process of evaluating and executing commands, and ensures correct handling of operator precedence and command grouping.

---

## 🧑‍💻 Implementation Details

The project was developed using **C** and includes the following core functionalities:

- **Input Parsing (AST)**: The input string is parsed into an AST, which is a tree structure representing commands, operators, and redirections. This makes it easier to execute commands in the correct order.
- **Command Execution**: For each command, the shell creates child processes using `fork()` and `execvp()` for execution. Redirection and piping are handled by manipulating file descriptors using `dup2()`.
- **Wildcards**: The shell uses the `glob()` function to expand wildcard characters into matching filenames.
- **Signal Handling**: Custom handling of signals like `SIGINT` (Ctrl+C) and `SIGQUIT` ensures that the shell behaves correctly when interrupted.

---

## 🔧 Files

- **`minishell.c`**: The main file containing the shell's execution loop and setup.
- **`parser.c`**: Functions for parsing user input and constructing the Abstract Syntax Tree (AST).
- **`exec.c`**: Functions for executing commands, handling redirections, and managing child processes.
- **`builtins.c`**: Implements the built-in commands such as `cd`, `echo`, and `exit`.
- **`wildcard.c`**: Handles wildcard expansion using `glob()`.
- **`signals.c`**: Custom signal handling logic for graceful shutdowns and managing `Ctrl+C` behavior.
- **`Makefile`**: Automates the build process for the project.

---

## 🧑‍🔧 Compilation & Setup

To compile and set up the project, follow these steps:

### 1. Clone the repository

```bash
git clone https://github.com/your-username/minishell.git
cd minishell
```

### 2. Compile the project
To compile the project and generate the executable, run:

```bash
make
```
This will create the minishell executable.

3. Clean up
To remove the object files:

```bash
make clean
```
To remove all compiled files, including the executable:

```bash
make fclean
```
To recompile everything from scratch:

```bash
make re
```

## 🧪 Example Usage
To use the minishell program, simply run it:

```bash
./minishell
```
This will launch the interactive shell. You can then enter commands like:

```bash
$ echo Hello World
$ cd /home/user
$ ls -l
```

## Wildcard Example
```bash
$ ls *.txt
```
This will list all files in the current directory with a .txt extension.

## Command Grouping Example
```bash
$ (cd /home; ls)
```
This will execute the cd command followed by ls in a subshell.

## 💡 Key Concepts & Challenges
AST Parsing: Handling complex input structures using an Abstract Syntax Tree (AST) for better command parsing and execution.
Process Management: Creating child processes with fork() and executing commands with execvp(), while managing redirection and piping.
Signal Handling: Handling interruptions like SIGINT without crashing the shell.
Wildcard Expansion: Expanding wildcards in file paths using glob().
Command Grouping: Allowing commands to be grouped and executed in a subshell with parentheses.

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

## 🤝 Collaboration
Feel free to contribute to this project! Fork it, submit issues, or open a pull request. If you have suggestions or feedback, don’t hesitate to reach out.

Happy coding! 🚀

markdown
Copy code
