# Distributed Version Control System
Goal :  Version | Track | Share

Structure:
* working directory
* staging
* snapshot in local repo
* github remote repo
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
## Comparing files
* Difference between WD and staging area: 
```
git diff <nameoffile>
```
* Difference between WD and last commit:
```
git diff HEAD <nameoffile>
```
* Difference between staged copy and last commit:
```
git diff --staged HEAD <nameoffile>
```
* Difference between WD and specific commit:
```
git diff <commitID> <filename>
```
To know the commit ID, use below command, which will give you all the commit IDs.
```
git log --oneline
```
* Difference between 2 branches:
```
git diff branch1 branch2
```
Note: space represents no change,  
\+ sign represents line added,  
\- sign represents line removed. 
* Difference between local repo and remote repo:
```
git diff <localrepobranchname> origin/<branchname>
```