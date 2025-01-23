# Vim Commands Documentation

This document provides a list of essential Vim commands with explanations and examples for quick reference.

## Table of Contents
1. [Basic Vim Commands](#basic-vim-commands)
2. [Navigation Commands](#navigation-commands)
3. [Editing Commands](#editing-commands)
4. [Searching and Replacing](#searching-and-replacing)
5. [File Operations](#file-operations)
6. [Miscellaneous Commands](#miscellaneous-commands)

## 1. Basic Vim Commands
| Command         | Description                               | Example / Usage                              |
|-----------------|-------------------------------------------|----------------------------------------------|
| `vim <file>`    | Open a file with Vim                      | `vim example.txt`                            |
| `:q`            | Quit Vim                                  | If no changes are made.                      |
| `:q!`           | Quit Vim without saving changes           | Use when you want to discard changes.        |
| `:w`            | Save changes                              | Save file without quitting.                  |
| `:wq`           | Save and quit                             | Save file and exit Vim.                      |
| `:x`            | Save and quit (same as `:wq`)              |                                              |
| `ZZ`            | Save and quit (same as `:wq`)              |                                              |

## 2. Navigation Commands
| Command         | Description                               | Example / Usage                              |
|-----------------|-------------------------------------------|----------------------------------------------|
| `h`             | Move cursor left                          |                                              |
| `j`             | Move cursor down                          |                                              |
| `k`             | Move cursor up                            |                                              |
| `l`             | Move cursor right                         |                                              |
| `w`             | Jump forward to the beginning of the next word |                                          |
| `b`             | Jump backward to the beginning of the previous word |                                     |
| `0`             | Move to the beginning of the current line  |                                              |
| `$`             | Move to the end of the current line        |                                              |
| `gg`            | Move to the first line of the document     |                                              |
| `G`             | Move to the last line of the document      |                                              |
| `Ctrl + f`      | Scroll one page forward                    |                                              |
| `Ctrl + b`      | Scroll one page backward                   |                                              |

## 3. Editing Commands
| Command         | Description                               | Example / Usage                              |
|-----------------|-------------------------------------------|----------------------------------------------|
| `i`             | Insert before the cursor                  | Switch to insert mode at the current cursor position. |
| `I`             | Insert at the beginning of the current line |                                          |
| `a`             | Append after the cursor                    | Switch to insert mode after the cursor.       |
| `A`             | Append at the end of the current line      |                                          |
| `o`             | Open a new line below the current line     |                                          |
| `O`             | Open a new line above the current line     |                                          |
| `x`             | Delete the character under the cursor     |                                          |
| `dd`            | Delete the current line                   |                                          |
| `yy`            | Yank (copy) the current line              |                                          |
| `p`             | Paste the yanked or deleted content after the cursor |                                    |
| `u`             | Undo the last change                      |                                          |
| `Ctrl + r`      | Redo the undone change                    |                                          |

## 4. Searching and Replacing
| Command         | Description                               | Example / Usage                              |
|-----------------|-------------------------------------------|----------------------------------------------|
| `/pattern`      | Search for a pattern                      | `/hello` searches for the word "hello".      |
| `?pattern`      | Search backward for a pattern             | `?world` searches for the word "world" backwards. |
| `n`             | Move to the next match of the search      |                                              |
| `N`             | Move to the previous match of the search  |                                              |
| `:%s/old/new/g` | Replace all occurrences of 'old' with 'new' |                                           |
| `:s/old/new/g`  | Replace all occurrences of 'old' with 'new' in the current line |                        |
| `:s/old/new/c`  | Replace with confirmation for each occurrence | `:s/foo/bar/c` asks for confirmation before each replacement. |

## 5. File Operations
| Command         | Description                               | Example / Usage                              |
|-----------------|-------------------------------------------|----------------------------------------------|
| `:e <filename>` | Open a file                              | `:e example.txt`                             |
| `:w <filename>` | Save the file with a new name             | `:w newfile.txt`                             |
| `:saveas <filename>` | Save the file with a new name        | Same as `:w <filename>`                      |
| `:sp`           | Split window horizontally                 | Open a new window in a horizontal split.     |
| `:vsp`          | Split window vertically                   | Open a new window in a vertical split.       |

## 6. Miscellaneous Commands
| Command         | Description                               | Example / Usage                              |
|-----------------|-------------------------------------------|----------------------------------------------|
| `:set number`   | Show line numbers                         | Display line numbers in the left margin.     |
| `:set nonumber` | Hide line numbers                         | Disable the display of line numbers.         |
| `:set relativenumber` | Show relative line numbers          | Line numbers displayed relative to the cursor position. |
| `:syntax on`    | Enable syntax highlighting                | Turn on syntax highlighting.                 |
| `:syntax off`   | Disable syntax highlighting               | Turn off syntax highlighting.                |

## Conclusion
This document provides an overview of some of the most common Vim commands. For more advanced functionality, consult the Vim help system by typing `:help` followed by the command you need help with.

Happy editing!

