---
title: "Introduction to Bash"
date: 2024-10-29 12:00:00 +0530
category: [blogs]
author: "Muhammed Sahl T V M"
excerpt: "A brief description of your post."
---

# Automating with Bash: A Beginner's Guide to Scripting and Path Management

## Introduction

If you're comfortable with basic Linux commands, scripting with Bash is a natural next step. Bash scripting allows you to combine commands and automate tasks, making your Linux experience more efficient and powerful. This guide covers essential concepts for beginners, including script structure, path usage, variables, and some common tasks.

## Why Learn Bash Scripting?

Bash scripting is like creating a to-do list for your computer, where each command is executed sequentially without needing manual input. This is especially useful for repetitive tasks, such as managing files, monitoring system health, or performing backups.

## 1. Basics of Bash Scripting

### Creating Your First Script

A Bash script is simply a text file containing a series of commands. Let's create a basic script:

1. Open a terminal and use a text editor (like nano) to create a file with a `.sh` extension:

   ```bash
   nano hello.sh
   ```

2. At the top of your file, add the shebang `#!/bin/bash` to specify that Bash should interpret this file.

3. Type a simple command, such as printing text to the screen:

   ```bash
   #!/bin/bash
   echo "Hello, world!"
   ```

4. Save the file and make it executable:

   ```bash
   chmod +x hello.sh
   ```

5. Run the script by typing:

   ```bash
   ./hello.sh
   ```

   This script outputs "Hello, world!" to the terminal. Every Bash script starts with a shebang (`#!/bin/bash`) to tell the system it's a script and should be run in Bash.

## 2. Using Variables in Scripts

Variables allow you to store information and reuse it throughout your script.

```bash
#!/bin/bash

greeting="Hello, world!"
echo $greeting
```

In this example, `$greeting` holds the text "Hello, world!". You can use this variable multiple times by referencing it with a `$` symbol.

### Getting User Input

Use `read` to get user input and store it in a variable.

```bash
#!/bin/bash

echo "Enter your name:"
read name
echo "Hello, $name!"
```

This script prompts the user to enter their name and greets them using that input.

## 3. Working with Paths

### Absolute and Relative Paths

- Absolute paths start from the root directory `/`, such as `/home/user/documents`.
- Relative paths start from the current directory, using symbols like `.` (current directory) and `..` (parent directory).

Example:

```bash
#!/bin/bash

echo "Current directory:" $(pwd)
echo "Listing files in home directory:"
ls /home/user  # Absolute path
ls ../         # Relative path (parent directory)
```

### Adding Directories to Your PATH

The `PATH` variable tells Linux where to look for commands. To run scripts from any directory without typing the full path, you can add a directory to the `PATH`.

1. Edit your shell profile (e.g., `~/.bashrc`):

   ```bash
   nano ~/.bashrc
   ```

2. Add the following line, replacing `/path/to/scripts` with the path where your scripts are stored:

   ```bash
   export PATH=$PATH:/path/to/scripts
   ```

3. Save and reload your profile:

   ```bash
   source ~/.bashrc
   ```

Now, you can run scripts in `/path/to/scripts` from any location by typing their names.

## 4. Common Bash Scripting Commands

### Looping

Loops are essential for repeating tasks. Here are two types of loops commonly used in Bash scripting:

#### `for` Loop

```bash
#!/bin/bash

for i in 1 2 3 4 5
do
  echo "Iteration $i"
done
```

#### `while` Loop

```bash
#!/bin/bash

counter=1
while [ $counter -le 5 ]
do
  echo "Iteration $counter"
  ((counter++))
done
```

### Conditionals

`if` statements let you run commands based on conditions.

```bash
#!/bin/bash

echo "Enter a number:"
read number

if [ $number -gt 10 ]; then
  echo "The number is greater than 10."
else
  echo "The number is 10 or less."
fi
```

### Functions

Functions group commands together, making scripts easier to read and manage.

```bash
#!/bin/bash

greet_user() {
  echo "Hello, $1!"
}

echo "Enter your name:"
read name
greet_user $name
```

In this script, `greet_user` is a function that takes a parameter and greets the user with the provided name.

## 5. Practical Bash Script Examples

### Automating File Backups

A script to copy files from one directory to a backup directory.

```bash
#!/bin/bash

source_dir="/home/user/documents"
backup_dir="/home/user/backup"

if [ ! -d "$backup_dir" ]; then
  mkdir -p "$backup_dir"
fi

cp -r "$source_dir"/* "$backup_dir"
echo "Backup completed."
```

### System Resource Monitoring

This script displays CPU and memory usage, which is helpful for basic system monitoring.

```bash
#!/bin/bash

echo "CPU Load: $(uptime)"
echo "Memory Usage:"
free -h
```

### Automated Disk Cleanup

A script to delete files older than 30 days in a specific directory.

```bash
#!/bin/bash

target_dir="/home/user/old_files"
find "$target_dir" -type f -mtime +30 -exec rm -f {} \;
echo "Old files deleted."
```

### Batch Renaming Files

A script to rename all `.txt` files in a directory by adding a timestamp prefix.

```bash
#!/bin/bash

for file in *.txt; do
  mv "$file" "$(date +%Y%m%d)_$file"
done
echo "Files renamed."
```

## 6. Debugging Bash Scripts

Bash provides ways to debug your scripts. You can add `set -x` at the beginning of your script to see each command as it's executed.

Example:

```bash
#!/bin/bash
set -x  # Enable debugging

echo "Hello, world!"

# Use set +x to disable debugging after a specific section of your script
```

## 7. Recommended Resources for Bash Scripting

Learning to write efficient scripts takes time and practice. Here are a few resources to deepen your understanding:

- Security Blue Team: Check out their Bash Scripting Basics certification, perfect for beginners wanting structured learning.
- Linux Documentation Project: An in-depth resource covering everything Linux, including scripting.
- Bash Academy: A site dedicated to Bash scripting tutorials and exercises.

## Conclusion

This guide covered the fundamentals of Bash scripting, including creating scripts, using paths, working with variables, and common scripting tasks. Each concept included here is foundational, and with practice, you'll be able to create powerful scripts that can automate repetitive tasks, manage files, and streamline your workflow.