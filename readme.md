# Git Cheatsheet

A list of git commands I use regularly. I tend to forget some of these so it's nice to have this in one place for easy reference.

## Setup

**Create a new local repo**

``` bash
git init
```

**Clone an existing repo**

``` bash
git clone git@github.com:username/repo-name.git
```

**Add a remote repo**

``` bash
git remote add origin https://github.com/username/repo-name.git
```

**Pushes and sets up an upstream reference for the branch `branch-name`**

``` bash
git push -u origin branch-name
```

---

## Undo

**Undo last commit**

Removes all staged and unstaged changes to tracked files:

``` bash
git reset --hard HEAD^
# OR
git reset --hard HEAD~1
```

It may be better use `--soft` flag, as it keeps the changes (leaves all your changed files *"Changes to be committed"*) so you can add more files, change files, etc. and commit later.

``` bash
git reset --soft HEAD^
# OR
git reset --soft HEAD~1
```

The `^` and `~1` is the number of commits to undo. `^^^` and `~3` removes the last 3 commits.

**Unstage files**

`git reset <file>` is the opposite of `git add <file>`.

``` bash
git reset filename.ext
```

---

## Committing

**Add all current changes to next commit**

``` bash
git add .
```

**Add some changes in file to next commit**

``` bash
git add -p filename.ext
```

**Add file to last commit**

In the case you commit and realise you forgot to add some file immediately:

``` bash
git add file-that-i-added-already.txt
git commit -m 'Add new file'

git add file-that-i-forgot.txt
git commit --amend --no-edit
```

**Commit all local changes**

``` bash
git commit -am 'Commit message'
```

**Change commit message**

``` bash
git commit --amend
```

---

## Branches

**Create and check out a new branch**

``` bash
git checkout -b new-branch
```

**List local branches**

``` bash
git branch
```

**List remote branches**

``` bash
git branch -r
```

**Switch to another branch**

``` bash
# switch to master branch
git checkout master
```

**Rename local branch**

``` bash
# rename current branch
git branch -m new-name
# if you're on a different branch
git branch -m old-name new-name
```

**Delete a branch locally**

``` bash
git branch -d branch-to-delete
```

**Delete a branch remotely**

``` bash
git push origin :branch-to-delete
# OR
git push origin --delete branch-to-delete
```

---

## Tags

**Mark the current commit with a tag**

``` bash
git tag 0.1.0
```

**Push all tags to origin**

``` bash
git push origin --tags
```

**Delete a tag locally**

``` bash
git tag -d 0.1.0
```

**Delete a tag remotely**

``` bash
git push origin :refs/tags/0.1.0
# OR
git push origin --delete 0.1.0
```

---

## History

**Show all commit starting with newest**

``` bash
git log
```

**Show the commits and changes for a specific file**

``` bash
git log -p filename.ext
```

**Show all branches and commits one line per commit**

``` bash
git log --oneline --decorate
```

**Show all branches and commits in a nicely formatted way**

``` bash
git log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(dim white) - %an%C(reset)%C(bold yellow)%d%C(reset)' --all
```

---

## Remotes

**Add new remote repo**

``` bash
git remote add remote-name remote-url
```

**List all remotes**

``` bash
git remote -v
```

**Set new remote URL**

``` bash
git remote set-url origin https://github.com/new-repo-url
```

**Remove remote**

``` bash
git remote rm origin
```

---

**Push different local branches to Heroku/master**

``` bash
git push heroku yourbranch:master
```
