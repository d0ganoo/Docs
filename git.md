[JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [Git](https://github.com/d0ganoo/Docs/blob/master/git.md)  

* * * 

Configuration
---
Configure user information for all local repositories

<code>git config --global user.name "[name]"</code><br>
Sets the name you want attached to your commit transactions

<code>git config --global user.email "[email address]"</code><br>

<code>git config --global color.ui auto</code><br>
Enables helpful colorization of command line output

Create repositories
---
Start a new repository or obtain one from an existing URL

<code>git init [project-name]</code><br>
Creates a new local repository with the specified name

<code>git clone [url]</code><br>
Downloads a project and its entire version history

Add files and commit
---
Review edits and craft a commit transaction

<code>git status</code><br>
Lists all new or modified files to be committed

<code>git diff</code><br>
Shows file differences not yet staged

<code>git add [file]</code><br>
Snapshots the file in preparation for versioning

<code>git diff --staged</code><br>
Shows file differences between staging and the last file version

<code>git reset [file]</code><br>
Unstages the file, but preserve its contents

<code>git commit -m "[descriptive message]"</code><br>
Records file snapshots permanently in version history

Branches
---
Name a series of commits and combine completed efforts
Sets the email you want attached to your commit transactions

<code>git branch</code><br>
Lists all local branches in the current repository

<code>git branch [branch-name]</code><br>
Creates a new branch

<code>git checkout [branch-name]</code><br>
Switches to the specified branch and updates the working directory

<code>git merge [branch]</code><br>
Combines the specified branch’s history into the current branch

<code>git branch -d [branch-name]</code><br>
Deletes the specified branch

Refactor files
---
Relocate and remove versioned files

<code>git rm [file]</code><br>
Deletes the file from the working directory and stages the deletion

<code>git rm --cached [file]</code><br>
Removes the file from version control but preserves the file locally

<code>git mv [file-original] [file-renamed]</code><br>
Changes the file name and prepares it for commit

See history
---
Browse and inspect the evolution of project files

<code>git log</code><br>
Lists version history for the current branch

<code>git log --follow [file]</code><br>
Lists version history for a file, including renames

<code>git diff [first-branch]...[second-branch]</code><br>
Shows content differences between two branches

<code>git show [commit]</code><br>
Outputs metadata and content changes of the specified commit

Ignore files
---
Exclude temporary files and paths
```
*.log
build/
temp-*
```
A text file named .gitignore suppresses accidental versioning of
files and paths matching the specified patterns

<code>git ls-files --other --ignored --exclude-standard</code><br>
Lists all ignored files in this project

Redo commits
---
Erase mistakes and craft replacement history

<code>git reset [commit]</code><br>
Undoes all commits after [commit] , preserving changes locally

<code>git reset --hard [commit]</code><br>
Discards all history and changes back to the specified commit

Stash changes
---
Shelve and restore incomplete changes

<code>git stash</code><br>
Temporarily stores all modified tracked files

<code>git stash pop</code><br>
Restores the most recently stashed files

<code>git stash list</code><br>
Lists all stashed changesets

<code>git stash drop</code><br>
Discards the most recently stashed changeset

Synchronize changes
---
Register a repository bookmark and exchange version history

<code>git fetch [bookmark]</code><br>
Downloads all history from the repository bookmark

<code>git merge [bookmark]/[branch]</code><br>
Combines bookmark’s branch into current local branch

<code>git push [alias] [branch]</code><br>
Uploads all local branch commits to GitHub

<code>git pull</code><br>
Downloads bookmark history and incorporates changes
