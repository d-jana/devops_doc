## What is Git and why it is used?
Git is a version control system for tracking changes in computer files and coordinating work on those files among multiple people. 
It is primarily used for source code management in software development, but it can be used to keep track of changes in any set of files.
It also as a DevOps tools

## What is Staging area in GIT?
The working area is where files that are not handled by git. These files are also referred to as **untracked files**. **Staging area** is files that are going to be a part of the next commit, which lets git know what changes in the file are going to occur for the next commit.
##
##

```
To use multiple file write each file with space to any command which take file name. like:

git add file1 file2 file3 ...
```

### SETUP & INIT

set automatic command line coloring for Git for easy reviewing
```
git config --global color.ui auto
```
retrieve an entire repository from github
```
git clone [repo url]
```
initialize an existing directory as a Git repository
```
git init
```

### STAGE & COMMIT

shows the current state of your Git working directory and staging area
```
git status
```
Add files to the staging area for next commit
```
git add [file]
```
unstage a file from staging area
```
git reset [file]
```
clean a current commit 
```
git reset --soft [alias]/[branch]
```
restore the uncommitted local changes of files
```
git restore [file]
```
commit your staged content. commit is the term used for saving changes
```
git commit -m “[descriptive message]”
```

### PUSH & PULL

add a git URL as an alias
```
git remote add [alias] [repo url]
```
Transmit local branch commits to the remote repository branch
```
git push [alias] [branch]
```
fetch and merge any commits from the tracking remote branch
```
git pull
```

### BRANCH & MERGE

show all branches. a * will appear next to the currently active branch
```
git branch
```
create a new branch. branch will be made after commit
```
git branch [branch-name]
```
switch to another branch
```
git checkout [branch-name]
```
merge current branch from a remote branch
```
git merge [alias]/[branch]
```
delete a branch from local and remote

  * from local
    ```
    git branch -d [branch]
    ```
    
  * from remote
    ```
    git push origin --delete [branch]
    ```
    

### INSPECT & COMPARE

show the commit history for the currently active branch
```
git log
```
show commit history of a particular file
```
git log --follow [file]
```
show changes to files in the worked area (after staged not showing diff)
```
git diff
```
show changes to files in the staged area (after commit not showing diff)
```
git diff --staged
```
show diff between two branch
```
git diff [banchA] [branchB]

show the diff of what is in branchA that is not in branchB
```

### REMOVE & IGNORING

Removes the file only from the Staging area, but not from the working area. After commit and push it will be remove from repo
```
git rm [file] --cached
```
Recursively removes folder only from the Git repository, but not from the working area. After commit and push it will be remove from repo
```
git rm -r [folder] --cached
```
Ignore a file or folder on git add. Create **.gitignore** file in project root directory and write content like this -
```
# If want to ignore everything
*
# If want to ignore file or folder just write file or folder name
logs
.idea
# Allow those folder which don't want to ignore
!src
!build

```
