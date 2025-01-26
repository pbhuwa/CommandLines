Here's a formatted version of the steps for creating an alias using `vim`:

### Alias Command Setup:

**Step 1: Open the `.bashrc` file in `vim`:**
```bash
vi ~/.bashrc
```

**Step 2: Enter insert mode in `vim` (press `i`):**
- This allows you to make changes to the file.

**Step 3: Add the alias:**
```bash
alias <name>="command"
```
- Replace `<name>` with your desired alias name.
- Replace `command` with the full command you want to alias.

**Step 4: Return to normal mode (press `Esc`):**
- This allows you to issue commands in `vim`.

**Step 5: Save the file and quit `vim`:**
```bash
:wq
```
- `:w` writes the changes.
- `:q` quits `vim`.

**Step 6: Reload the `.bashrc` to apply changes:**
```bash
source ~/.bashrc
```

That's it! Now you can use your new alias in the terminal.