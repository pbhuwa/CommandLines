# Linux Commands Cheat Sheet

## Basic Commands

### `pwd` - Print Working Directory
- **Usage**: `pwd`
- **Description**: Displays the full path of the current directory.

### `ls` - List Directory Contents
- **Usage**: `ls [options] [directory]`
- **Description**: Lists files and directories within a directory.
- **Common Options**:
  - `-l`: Long format listing.
  - `-a`: Include hidden files.
  - `-h`: Human-readable file sizes.

### `cd` - Change Directory
- **Usage**: `cd [directory]`
- **Description**: Changes the current working directory.
- **Examples**:
  - `cd /home`: Go to the `/home` directory.
  - `cd ..`: Move to the parent directory.

### `mkdir` - Make Directory
- **Usage**: `mkdir [options] [directory_name]`
- **Description**: Creates a new directory.
- **Common Options**:
  - `-p`: Create parent directories as needed.

### `rm` - Remove Files or Directories
- **Usage**: `rm [options] [file/directory]`
- **Description**: Deletes files or directories.
- **Common Options**:
  - `-r`: Recursively delete directories.
  - `-f`: Force delete without confirmation.

### `cp` - Copy Files or Directories
- **Usage**: `cp [options] source destination`
- **Description**: Copies files or directories.
- **Common Options**:
  - `-r`: Copy directories recursively.
  - `-v`: Verbose mode.

### `mv` - Move or Rename Files
- **Usage**: `mv source destination`
- **Description**: Moves or renames files or directories.

### `touch` - Create Empty Files
- **Usage**: `touch [file_name]`
- **Description**: Creates an empty file or updates the timestamp of an existing file.

---

## File Permissions and Ownership

### `chmod` - Change Permissions
- **Usage**: `chmod [options] mode file`
- **Description**: Changes file permissions.
- **Examples**:
  - `chmod 755 file`: Gives read, write, and execute permissions to the owner, and read and execute to others.

### `chown` - Change Ownership
- **Usage**: `chown [owner][:group] file`
- **Description**: Changes the owner and/or group of a file.

---

## Viewing and Editing Files

### `cat` - View File Content
- **Usage**: `cat [file]`
- **Description**: Concatenates and displays the content of files.

### `nano` - Text Editor
- **Usage**: `nano [file]`
- **Description**: Opens a file in the Nano text editor.

### `vim` - Advanced Text Editor
- **Usage**: `vim [file]`
- **Description**: Opens a file in the Vim text editor.

### `head` - View Start of a File
- **Usage**: `head [options] [file]`
- **Description**: Displays the first 10 lines of a file by default.
- **Common Options**:
  - `-n`: Specify the number of lines to display.

### `tail` - View End of a File
- **Usage**: `tail [options] [file]`
- **Description**: Displays the last 10 lines of a file by default.
- **Common Options**:
  - `-f`: Follow the file as it grows (e.g., log files).

---

## Process Management

### `ps` - View Processes
- **Usage**: `ps [options]`
- **Description**: Displays information about active processes.
- **Common Options**:
  - `-e`: Show all processes.
  - `-f`: Full format listing.

### `top` - Monitor System Resources
- **Usage**: `top`
- **Description**: Displays real-time information about system processes and resource usage.

### `kill` - Terminate Processes
- **Usage**: `kill [PID]`
- **Description**: Sends a signal to terminate a process.

### `htop` - Interactive Process Viewer
- **Usage**: `htop`
- **Description**: Interactive process viewer (must be installed separately).

---

## Networking

### `ping` - Test Network Connectivity
- **Usage**: `ping [host]`
- **Description**: Sends ICMP echo requests to test connectivity.

### `curl` - Transfer Data from URLs
- **Usage**: `curl [options] [URL]`
- **Description**: Transfers data from or to a server.

### `wget` - Download Files
- **Usage**: `wget [URL]`
- **Description**: Downloads files from the internet.

---

## Disk Usage

### `df` - Disk Free Space
- **Usage**: `df [options]`
- **Description**: Displays disk space usage of file systems.
- **Common Options**:
  - `-h`: Human-readable format.

### `du` - Disk Usage
- **Usage**: `du [options] [directory/file]`
- **Description**: Displays disk usage of files and directories.
- **Common Options**:
  - `-h`: Human-readable format.
  - `-s`: Display total size of a directory.

---

## Search and Find

### `find` - Search for Files
- **Usage**: `find [path] [options]`
- **Description**: Searches for files and directories.
- **Examples**:
  - `find / -name file.txt`: Search for `file.txt` in the root directory.

### `grep` - Search Inside Files
- **Usage**: `grep [options] pattern [file]`
- **Description**: Searches for patterns in files.
- **Common Options**:
  - `-i`: Case insensitive.
  - `-r`: Recursive search.

---

## Archiving and Compression

### `tar` - Archive Files
- **Usage**: `tar [options] [archive_name] [files/directories]`
- **Description**: Creates or extracts archives.
- **Common Options**:
  - `-cvf`: Create an archive.
  - `-xvf`: Extract an archive.
  - `-z`: Use gzip for compression.

### `zip` / `unzip` - Compress and Extract Files
- **Usage**:
  - Compress: `zip [archive_name.zip] [files]`
  - Extract: `unzip [archive_name.zip]`
- **Description**: Compresses or extracts files using the ZIP format.

---

## System Information

### `uname` - System Information
- **Usage**: `uname [options]`
- **Description**: Displays system information.
- **Common Options**:
  - `-a`: All system information.

### `uptime` - System Uptime
- **Usage**: `uptime`
- **Description**: Shows how long the system has been running.

### `whoami` - Current User
- **Usage**: `whoami`
- **Description**: Displays the current logged-in user.

---

## Package Management (Debian/Ubuntu)

### `apt-get` - Manage Packages
- **Usage**: `apt-get [command] [package_name]`
- **Description**: Manages packages on Debian-based systems.
- **Common Commands**:
  - `install`: Install a package.
  - `remove`: Remove a package.
  - `update`: Update package lists.
  - `upgrade`: Upgrade all packages.

---

This cheat sheet provides an overview of essential Linux commands. For detailed usage, refer to the manual pages using `man [command]`. Example: `man ls`.
