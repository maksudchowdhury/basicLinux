<h2 align=center> Redirecting Output to File or Program </h2>

### Redirecting Standard Output to a File
To redirect the output of a command to a file, use the `>` operator.

```bash
ls > file_list.txt
```

This command will save the output of `ls` to `file_list.txt`.

### Appending Output to a File
To append the output to an existing file, use the `>>` operator.

```bash
echo "New line" >> file_list.txt
```

This command will add "New line" to the end of `file_list.txt`.

### Redirecting Standard Error to a File
To redirect error messages, use `2>`.

```bash
ls non_existing_file 2> error_log.txt
```

This command will save the error message to `error_log.txt`.

### Redirecting Both Standard Output and Error
To redirect both output and error, use `&>`.

```bash
ls existing_file non_existing_file &> combined_log.txt
```

This command will save both the output and error messages to `combined_log.txt`.

## Practice: I/O Redirection and Pipelines

### Using Pipelines
Pipelines allow you to pass the output of one command as input to another using the `|` operator.

```bash
ls -l | grep ".txt"
```

This command lists all `.txt` files in the current directory.

### Combining Redirection and Pipelines
You can combine redirection and pipelines to filter and save output.

```bash
ls -l | grep ".txt" > txt_files_list.txt
```

This command saves the list of `.txt` files to `txt_files_list.txt`.

## Editing Text Files from the Shell Prompt

### Using `nano` Editor
`nano` is a simple text editor.

```bash
nano example.txt
```

This command opens `example.txt` in `nano`.

### Using `cat` to Create a File
You can create a file using `cat`.

```bash
cat > newfile.txt
```

Type your text and press `Ctrl+D` to save.

## Practice: Editing Files with Vim

### Opening a File in Vim
To open a file in `vim`, use:

```bash
vim example.txt
```

### Basic Vim Commands
- `i`: Enter insert mode.
- `Esc`: Exit insert mode.
- `:w`: Save the file.
- `:q`: Quit `vim`.
- `:wq`: Save and quit.

### Sample Vim Session
```bash
vim example.txt
```

Inside `vim`:
```
i
This is a new line.
Esc
:wq
```

## Editing Text Files with a Graphical Editor

### Using `gedit`
`gedit` is a graphical text editor.

```bash
gedit example.txt &
```

This command opens `example.txt` in `gedit`.

## Practice: Copying Text Between Windows

### Using `tmux` for Multiple Windows
`tmux` allows you to manage multiple terminal windows.

```bash
tmux
```

Inside `tmux`, split the window:

```bash
Ctrl+B, "
```

To copy text, enter copy mode:

```bash
Ctrl+B, [
```

Navigate and select text, then press `Enter` to copy. Paste with:

```bash
Ctrl+B, ]
```

## Lab: Creating, Viewing, and Editing Text Files

### Creating a File
```bash
touch labfile.txt
```

### Viewing a File
```bash
cat labfile.txt
```

### Editing a File with `nano`
```bash
nano labfile.txt
```

### Editing a File with `vim`
```bash
vim labfile.txt
```

### Editing a File with `gedit`
```bash
gedit labfile.txt &
```
