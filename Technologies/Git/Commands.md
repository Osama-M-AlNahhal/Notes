----
# Add

![[git commands 1.png]]

```git
git add file.txt
```
*to add everything in the repo -> replace `file.txt` with `.`*

this has 2 functionalities:
	1. if the file is not tracked before, it initiates its tracking
	2. if the file is already tracked, it stages it

## Undo tracking
```git
git rm --cached file.txt
```

## Restore from index
```git
git restore file.txt
```
*note: this will discard any changes you've made to the file since the last time you added it to the index*

## Undo staging then restore previous staged version
```git
git restore --staged file.txt
git restore file.txt
```

---

# Checking files in WD, Index and Repo

## WD

```widnows
dir
```

```linux
ls
```

## Index (Staging Area)
```widnows-and-linux
git ls-files
```
- *to see info, permissions, the sha of the file as well as the neme -> we add the `-s` flag*

## Repo 
*note: this is not important to our workflow, and therefor there's no defined command for it, but we can do it using the following method*
```linux
find .git/objects/ -type f
```


---

# Status
*check the status of the current working directory to see if there's any changes or untracked files*

```git
git status
```
*note: to get a simplified view of the status -> add the `-s` flag*

---

# Log
*get a log of all the commits in this repo*

```git
git log
```
****Note: there are alot of different filtering tags that can be added after this command***
- *to get a short version of the log -> add `--oneline`*
- *to get the last x number of commits -> add `-x`*


---

# reflog
*this shows the log of the changes done on the time line (like fasting forward or rolling back)*

```git
git reflog
```


---

# Diff

![[git commands 3.png]]

*difference between the working directory and the index*
```git
git diff
```


*difference between the index and the repo*
```git
git diff --staged
```


*difference between two commits* (using their sha)
```git
git diff 2d61f21..a5b5f79
```

---

# Commit

![[git commands 2.png]]

```git
git commit -m "commit info"
```

**To commit a file without staging it (2 steps in 1)
```git
git commit -am "commit message"
```
*note: the a flag is for adding, the m flag is for the message*

*to edit the message of the last commit*
```git
git commit --amend
```

# reset
- *this is done by moving the pointer (sha) inside the `HEAD` to be pointing at the commit we want*
- *replace `x` with the number of commits you want to roll back on*

![[git commands 4.png]]

- this resets the index, not the work tree
```git
git reset HEAD~x
```

- *if we want it to affect the work tree immedietly (very dangerous)*
```git
	git reset --hard HEAD~1 
```


---

# Show

*this is used to show the changes in a commit (by using the commit's `sha`*
```git
git show c5sfc56dfc1
```

---

# Tag
*tags are like a pointer with a name, we can use them to note new versions of our software*
*by adding the `-a` git creates an enitrely new `tagged annotation` object*

```git
git tag -a v2.0 -m "version 2.0"
```


---

# Branch

## create new branch

```git
git branch branchName
```
*this basically just creates a pointer called `branchName` and places is on the current commit, then we switch to `branchName` and add changes and commit, this commit will be a new commit object, and the `branchName` pointer will move to point at this new commit*

## switch to this new branch

```git
git switch branchName
```

## show available branches

```git 
git branch
```

## Deleting a branch
*after merging a branch to another, you no longer need the 'tag' that is that merged branch, so you can delete it using the following*

```git
git branch -d branchName
```


---

# Merge

*the idea of merging is that you switch into the branch you want to merge your other branch into, then by merging either you have a linear path from the current branch to the branch you want to merge, so you fast forward the HEAD pointer from the current branch to the branch you wanted to merge, making it the current HEAD, or if there was a divergence, then an entirely new commit is created, and both branches are merged into that new commit, if there was a conflict then git will ask you which branch you want to choose between the two conflicted branches*

```git
git merge branchName
```


---

# Working with Remotes

## Showing Your Remotes
```git
git clone https://github.com/schacon/ticgit  
git remote
git remote -v
```


## Add a remote to an existing repo
```git
git remote add [shortname] [url]
```


## Fetching from Remote
*fetches any new work that has been pushed to that server since you cloned (or last fetched from) it*
```git
git fetch [remote-name]
```
**IMPORTANT:** *Fetch doesn’t automatically merge it with any of your work or modify what you’re currently working on. You have to merge it manually into your work when you’re ready.*


## Pushing to Your Remotes
*Means uploading any changes you have made to the remote that*
```git
git push [remote-name] [branch-name]
```


## Inspecting a Remote
*See more information about a particular remote*
```git
git remote show [remote-name]
```


## Renaming Remotes
```git
git remote rename [current-remote-name] [new-remote-name]
```


## Removing Remotes
*If you want to remove a remote for some reason—you’ve moved the server or are no longer using a particular mirror, or perhaps a contributor isn’t contributing anymore*
```git
git remote rm [remote-name]
```