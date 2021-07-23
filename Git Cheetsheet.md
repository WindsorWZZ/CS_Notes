# Git Handbook
## Introduction
The handbook is organized by tasks that we frequently meet with in daily work. You can find them in the directory and follow the guide step by step.  
## Tasks
### 1. Download a repository
```zsh
git clone git@xxx.git
```

### 2. Create a branch
```zsh
# create and checkout new_branch （locally）
git checkout -b new_branch

# push to remote new_branch
git push origin local_branch:remote_branch
```

### 3. Get a branch
```zsh
# in one command:
git checkout -b mybranch origin/branch
```

### 4. Using diff
```zsh
# diff workspace & Index
git diff

# diff local branch1 & remote branch2 (stat only display files)
git diff branch1 origin/branch2 --stat

# diff a file in two branches
git diff branch1 branch2 filename
```

### 5. Push local revisions to a branch
```zsh
# new commits
git push

# conflict commits (replace remote branch)
git push -f
```

### 6. Merge branches
```zsh
# 1. update local master repo
# switch to "master"
git checkout master

# get latest version from master (replace local files in workspace)
# equals to 'git fetch' + 'git merge FETCH_HEAD'
git pull

# 2. merge & store
# switch to "dev" branch
git checkout {dev}

# merge "master" to "dev"
git merge master
# or
git rebase master

# solve conflicts
# step 1 delete remarks & select right contents
# step 2 add merged files
git add .
#step 3 finish rebase
git rebase --continue

# push the merged "dev" branch to remote
git push
```

### 7. Get files from another branch
```zsh
git checkout current_branch
git checkout source_branch file_path
git commit -m "get file_path from source branch"
```

### 8. Squash commits to one
Solution 1:
```zsh
# rollback commit (changes still in index)
# param could be: 1. a branch (go to the latest commit) 2. a commit
git reset --soft {param}

# re-commit
git commit -m "merged commit"
```
Solution 2:
```zsh
git log # view the commits & copy a commit id

git rebase -i {commit_id or branch_name} # rebase to a commit or branch

# modify rebase file:
pick {commit_1}
reword {commit_2}
squash {commit_3}
# the commit_1 will be saved, the commit 2 will be saved and renamed, commit 3 will be squashed
```

### 9. Rollback a branch
```zsh
git checkout the_branch
git pull
git branch the_branch_backup # back up current branch
git reset --hard the_commit_id # rollback current branch
git push origin :the_branch # delete remote the_branch
git push origin the_branch # create the_branch using the local rollbacked branch
git push origin :the_branch_backup # everything ok, delete backup branch
git branch -D the_branch_backup # delete local branch
```


##