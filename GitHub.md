###### **INSTALLATION & GUIS**

With platform specific installers for Git, GitHub also provides the
ease of staying up-to-date with the latest releases of the command
line tool while providing a graphical user interface for day-to-day
interaction, review, and repository synchronization.

###### **SETUP**

Configuring user information used across all local repositories

> 📋 Set a name that is identifiable for credit when review version history
>
> ```
> git config --global user.name “[firstname lastname]”
> ```

> 📋 Set an email address that will be associated with each history marker
>
> ```
> git config --global user.email “[valid-email]”
> ```

> 📋 Set automatic command line coloring for Git for easy reviewing
>
> ```
> git config --global color.ui auto
> ```

###### **SETUP & INIT**

Configuring user information, initializing and cloning repositories

> 📋 Initialize an existing directory as a Git repository
>
> ```
> git init
> ```

> 📋 Retrieve an entire repository from a hosted location via URL
>
> ```
> git clone [url]
> ```

##### **STAGE & SNAPSHOT**

Working with snapshots and the Git staging area

> 📋 Show modified files in working directory, staged for your next commit
>
> ```
> git status
> ```

> 📋 Add a file as it looks now to your next commit (stage)
>
> ```
> git add [file]
> ```

> 📋 Unstage a file while retaining the changes in working directory
>
> ```
> git reset [file]
> ```

> 📋 diff of what is changed but not staged
>
> ```
> git diff
> ```

> 📋 diff of what is staged but not yet commited
>
> ```
> git diff --staged
> ```

> 📋 commit your staged content as a new commit snapshot
>
> ```
> git commit -m “[descriptive message]”
> ```

##### **BRANCH & MERGE**

Isolating work in branches, changing context, and integrating changes

> 📋 List your branches. a \* will appear next to the currently active branch
>
> ```
> git branch
> ```

> 📋 Create a new branch at the current commit
>
> ```
> git branch [branch-name]
> ```

> 📋 Switch to another branch and check it out into your working directory
>
> ```
> git checkout
> ```

> 📋 Merge the specified branch’s history into the current one
>
> ```
> git merge [branch]
> ```

> 📋 Show all commits in the current branch’s history:
>
> ```
> git log
> ```

##### **INSPECT & COMPARE**

Examining logs, diffs and object information

> 📋 show the commit history for the currently active branch
>
> ```
> git log
> ```

> 📋 show the commits on branchA that are not on branchB
>
> ```
> git log branchB..branchA
> ```

> 📋 show the commits that changed file, even across renames
>
> ```
> git log --follow [file]
> ```

> 📋 show the diff of what is in branchA that is not in branchB
>
> ```
> git diff branchB...branchA
> ```

> 📋 show any object in Git in human-readable format
>
> ```
> git show [SHA]
> ```

##### **TRACKING PATH CHANGES**

Versioning file removes and path changes

> 📋 delete the file from project and stage the removal for commit
>
> ```
> git rm [file]
> ```

> 📋 change an existing file path and stage the move
>
> ```
> git mv [existing-path] [new-path]
> ```

> 📋 show all commit logs with indication of any paths that moved
>
> ```
> git log --stat -M
> ```

##### **IGNORING PATTERNS**

Preventing unintentional staging or commiting of files

> Save a file with desired paterns as .gitignore with either direct string
> matches or wildcard globs.
>
> ```
> logs/
> *.notes
> pattern*/
> ```

> system wide ignore patern for all local repositories
>
> ```
> git config --global core.excludesfile [file]
> ```

##### **SHARE & UPDATE**

Retrieving updates from another repository and updating local repos

> 📋 add a git URL as an alias
>
> ```
> git remote add [alias] [url]
> ```

> 📋 fetch down all the branches from that Git remote
>
> ```
> git fetch [alias]
> ```

> 📋 merge a remote branch into your current branch to bring it up to date
>
> ```
> git merge [alias]/[branch]
> ```

> 📋 Transmit local branch commits to the remote repository branch
>
> ```
> git push [alias] [branch]
> ```

> 📋 fetch and merge any commits from the tracking remote branch
>
> ```
> git pull
> ```

##### **REWRITE HISTORY**

Rewriting branches, updating commits and clearing history

> 📋 apply any commits of current branch ahead of specified one
>
> ```
> git rebase [branch]
> ```

> 📋 clear staging area, rewrite working tree from specified commit
>
> ```
> git reset --hard [commit]
> ```

##### **TEMPORARY COMMITS**

Temporarily store modified, tracked files in order to change branches

> 📋 Save modified and staged changes
>
> ```
> git stash
> ```

> 📋 list stack-order of stashed file changes
>
> ```
> git stash list
> ```

> 📋 write working from top of stash stack
>
> ```
> git stash pop
> ```

> 📋 discard the changes from top of stash stack
>
> ```
> git stash drop
> ```
