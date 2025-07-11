# Shell

A lightweight Unix-like shell implementation with support for common shell features including piping, I/O redirection, environment variables, and command chaining.

## Features

- **Basic Shell Operations**:
  - Command execution (`ls`, `grep`, etc.)
  - Custom command prompt showing username and current directory
  - Error handling for invalid commands

- **Advanced Features**:
  - **Piping**: Command chaining with `|` (e.g., `ls | grep .txt`)
  - **I/O Redirection**:
    - Input redirection `<` (e.g., `sort < input.txt`)
    - Output redirection `>` (e.g., `ls > output.txt`)
    - Append redirection `>>` (e.g., `echo "text" >> file.txt`)
  - **Environment Variables**:
    - Variable assignment (`VAR=value`)
    - Variable expansion in `echo` (`echo $VAR`)
  - **Command Chaining**: Multiple commands with `;` separator

## Building and Running

1. Compile the shell:
   ```bash
   make
   ```

2. Run
   ./hy345sh

## Implementation Details

### Key Components

#### Command Parsing:
- Space-separated argument parsing  
- Special character handling (`|`, `>`, `<`, `>>`, `;`, `$`)  
- String trimming and sanitization  

#### Process Management:
- Fork-exec model for command execution  
- Proper process waiting and cleanup  
- File descriptor handling for I/O operations  

#### Memory Management:
- Fixed-size buffers for input and arguments  
- No dynamic memory allocation  

---

## Constants and Limits

| Item                          | Value               |
|-------------------------------|---------------------|
| Maximum input length          | `MAXCOM` (1000)     |
| Maximum commands in chain     | `MAXLIST` (100)     |
| Maximum directory path length | `MAXDIR` (1024)     |
| Maximum environment variables | `MAX_VARS` (100)    |
| Max variable name length      | `MAX_VAR_NAME` (50) |
| Max variable value length     | `MAX_VAR_VALUE` (1024) |

---

## Limitations

- No Background Processes: All commands run in foreground  
- No Built-in Commands: Relies on system commands (`/bin`)  
- No Command History: Previous commands aren't stored  
- No Tab Completion: Manual typing required  
- No Signal Handling: `CTRL+C` exits the shell  

---

## Error Handling

The shell provides basic error messages for:

- Command not found  
- Fork/exec failures  
- I/O redirection errors  
- Pipe creation failures  
- Invalid variable assignments  
