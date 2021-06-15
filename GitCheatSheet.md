# Distributed Version Control System
Goal :  Version | Track | Share  

Github is a hosting service for git repositories.  
Git is the tool, while GitHub is a  service to use git.

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
## Stage, Commit and Push
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
After commit, push your code to remote main branch.
```
git push origin main
```
## Branch & Merge
To isolate work in branches, change context, and integrate changes.  
To list your branches, use `git branch` . A * will appear next to the currently active branch.  
To rename a branch, use `git branch -m <oldname> <newname>`
To create a new branch:
```
git branch <branchname>
```
To switch to the new branch:
```
git checkout <branchname>
```
Shortcut for above to commands to create and switch to a new branch:
```
git checkout -b <branchname>
```
To push new file to new branch: 
```
git push --set-upstream origin <branchname>
```

To Merge:
```
git checkout main
git merge <branchname>
```
2 ways:
1. Fast-forward merge   
    Linear flow.    
    Changes are only done in feature branch and merged into main branch. No chance og getting any conflict into the code.  

2. Three way merge (Recursive strategy)   
    Non- linear flow.  
    Changes done in feature branch. Main branch is also developing. So there are chances of conflict. New Merge commit will be created and you have to resolve the commit manually.

## Delete Branch
```
git branch -d <branchname>
```
## Rebase
Rebase is a 2 step process.
1. Rebase your feature code on top of main branch.
```
git rebase main
```
2. Merge feature branch into main.
```
git merge feature
```
Try to use rebase only on local environment. Not recommended in remote repo because new commits are created when you rebase. History will not be maintained. Commit IDs are deleted. 

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
## Removing files
Use `git ls-files` to check what all files are added in your staged copy.
* Remove files from both staging and WD:
```
git rm <filename>
```
* Remove all the files from both staging and WD:
```
git rm -r
```
* Remove files only from staging:
```
git rm --cached <filename>
```
* Remove files only from WD:
```
rm <filename>
```
## Undo changes
To discard unstaged changes in the tracked files of working directory.  
Tracked files - Files that are added to the staging or local repo atleast.  
Unstaged changes - which are not added to staging area yet.
```
git checkout -- <filename>
```
## Reset Command
* To remove changes from staging area.
```
git reset <filename>
```
* To undo commits at repository level.
```
git reset <mode> <commitID>
```
mode represents whether changes are to remove from staging area or working directory or not. All commits above the mentioned commit ID will be removed.
3 types of modes:
1. mixed (default) - from local repo and staging.  
   -- `git reset <commitID>`
2. soft - only from local repo.  
   -- `git reset --soft <commitID>`
3. hard - changes are removed from local repo, stage and WD.  
   -- `git reset --hard <commitID>`