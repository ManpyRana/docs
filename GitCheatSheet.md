# Distributed Version Control System
Goal :  Version | Track | Share
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
If files are already in your local repo, you can use below command to stage and commit:
```
git commit -a -m "your message"
```
## Branch & Merge
To isolate work in branches, change context, and integrate changes.  
To list your branches, use `git branch` . A * will appear next to the currently active branch.  
To rename a branch, use `git branch -m <oldname> <newname>`
To creat a new branch:
```
git checkout -b <branchname>
git push origin <branchname>

```
To push changes to github: 
```
git push --set-upstream origin <branchname>
```

To Merge:
```
git checkout main
git merge <branchname>
```
## Stay updated with remote
To update your local repository to the newest commit :  
```
git pull
```

