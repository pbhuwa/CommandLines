###### **INSTALLATION & GUIS**
With platform specific installers for Git, GitHub also provides the
ease of staying up-to-date with the latest releases of the command
line tool while providing a graphical user interface for day-to-day
interaction, review, and repository synchronization.

###### **SETUP**
Configuring user information used across all local repositories
> 📋 Set a name that is identifiable for credit when review version history
> ```
> git config --global user.name “[firstname lastname]”
> ```

> 📋 Set an email address that will be associated with each history marker
> ```
> git config --global user.email “[valid-email]”
> ```

> 📋 Set automatic command line coloring for Git for easy reviewing
> ```
> git config --global color.ui auto
> ```

###### **SETUP & INIT**
Configuring user information, initializing and cloning repositories
> 📋 Initialize an existing directory as a Git repository
> ```
> git init
> ```

> 📋 Retrieve an entire repository from a hosted location via URL
> ```
> git clone [url]
> ```

##### **STAGE & SNAPSHOT**
Working with snapshots and the Git staging area
> 📋 Show modified files in working directory, staged for your next commit
> ```
> git status
> ```

> 📋 Add a file as it looks now to your next commit (stage)
> ```
> git add [file]
> ```

> 📋 Unstage a file while retaining the changes in working directory
> ```
> git reset [file]
> ```

> 📋 diff of what is changed but not staged
> ```
> git diff
> ```

> 📋 diff of what is staged but not yet commited
> ```
> git diff --staged
> ```

> 📋 commit your staged content as a new commit snapshot
> ```
> git commit -m “[descriptive message]”
> ```

##### **BRANCH & MERGE**
Isolating work in branches, changing context, and integrating changes
> 📋 List your branches. a * will appear next to the currently active branch
> ```
> git branch
> ```

> 📋 Create a new branch at the current commit
> ```
> git branch [branch-name]
> ```

> 📋 Switch to another branch and check it out into your working directory
> ```
> git checkout
> ```

> 📋 Merge the specified branch’s history into the current one
> ```
> git merge [branch]
> ```

> 📋 Show all commits in the current branch’s history:
> ```
> git log
> ```
