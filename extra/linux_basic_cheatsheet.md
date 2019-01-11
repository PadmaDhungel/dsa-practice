# Linux Basics Cheat Sheet
> *Handy for Git Bash users on Windows too!*

## Navigating the File System

- `pwd`  
  Print the current working directory (shows where you are).

- `ls`  
  List files and folders in the current directory.  
  Options:  
  - `ls -l` (detailed info)  
  - `ls -a` (include hidden files)

- `cd <directory>`  
  Change directory.  
  Examples:  
  - `cd ..` (go up one level)  
  - `cd ~` (go to home directory)  
  - `cd /` (go to root directory)

> **Note:** In Git Bash on Windows, file paths use Unix-style format, e.g., `/c/Users/YourName/Documents` instead of Windows-style `C:\Users\YourName\Documents`.
---

## Working with Files and Folders

- `mkdir <foldername>`  
  Create a new directory.

- `touch <filename>`  
  Create a new empty file.

- `rm <filename>`  
  Remove/delete a file.

- `rm -r <foldername>`  
  Remove a folder and its contents recursively.

- `cp <source_path> <destination_path>`  
  Copy a file or directory

- `mv <source_path> <destination_path>`  
  move and remame a file or directory
---

## Viewing File Content

- `cat <filename>`  
  Display the contents of a file.

- `head <filename>`  
  Show the first 10 lines of a file.

- `tail <filename>`  
  Show the last 10 lines of a file.

---

## Important Configuration Files (Common Locations)

- `/etc/`  
  System-wide configuration files folder.

- `~/.gitconfig`  
  Git configuration file for your user (in home directory).

- `~/.bashrc` or `~/.zshrc`  
  User shell configuration files.

- `~/.ssh`  
  Folder containing SSH keys and config (e.g., `id_rsa`, `id_rsa.pub`, `config`, `known_hosts`).
---

##  Quick Tips

- Use `clear` for keeping terminal clean
- Use `Tab` for auto-completion of commands and file/folder names.
- Use `Ctrl + C` to stop a running command.
- Use `history` to see previously run commands.

---