## Setup
Configuring user information used across all local repositories
```
git config --global user.name “[firstname lastname]”
```
```
git config --global user.email “[valid-email]”
```
## Initialise & Clone
```
git init
git clone <URL>
git pull
```
## Stage & Commit
To show modified files in working directory, staged for your next commit.
```
git status
```
Staging : To add a file to your next commit.
```
git add <filename>
```
To unstage, use below command: 
```
git reset <filename>
```
To commit your staged content :
```
git commit -m "descriptive message"
```
## Branch & Merge
To isolate work in branches, change context, and integrate changes.  
To list your branches, use `git branch` . A * will appear next to the currently active branch.  
To rename a branch, use `git branch -m <oldname> <newname>`
To creat a new branch:
```
git checkout -b <branchname>
```
To Merge:
```
git checkout main
git merge <branchname>
```
