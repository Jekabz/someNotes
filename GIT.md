GIT INSTRUCTIONS
================

#### GIT STAGING AREA:

* Buffer between working directory and project history
* Staging allows to group related changes before `commit`ing them to project history
####GIT CONFIG:

```bash
git config --global user.name "name-surname"
```

####CREATE NON BARE REPO IN WORKING DIRECTORY:

```bash
git init
git remote add <project_name or origin> <ssh or web address>
git clone <ssh or web address> #no real need for this, but it sets branch tracking automatically
```
####GITIGNORE:

* set up .gitignore:

```bash
touch .gitignore
```
* .gitignore contents:

```bash
$ cat.gitignore
```
* gitignore wildcards:

```
<fodername>/ #will ignore any folder with foldername
*.<extension> #ignores all files with this extension
<filename> #ignores file with filename
<filename>* #ignores filename with any extenson
```
####GIT ACTIONS:

* show changes in project directory and staging area:

```
git status
```
* if unwanted file is trackded (shows up in git status):

```
git rm --cached <file>
```
* add needed changes to Index:

```
git add <filename>
git add -A #adds all files
git add -p #begins an interactive staging session
```

* commit to Head (local repo). Commits the staged snapshot:

```
git commit -m "Commit message"
```

* commit to remote repo:

```
git branch --set-upstream-to=origin/master master #do the first time (?)
git pull #optional
git push
```

* overwrite unneeded changes in my local repo with remote repo, that also has some changes in it:

```
git stash save --keep-index
git stash drop
```
* git stash takes the dirty state of the project and saves it on a stack of unsaved changes that can be reappied at any time
* all stashes are saved on a stack, and they have a number {{0},{1},...,{n}}
```
git stash #saves the "dirty" changes
git stash list #shows stashes on stack
git stash apply #applies the last stashed changes
git stash apply stash@{2} #applies changes in {2} stash
git stash drop #will drop the latest (?) saved stash
git stash drop stash@{n} #remves the {n} stash from stack
git stash pop #applies the stash and immediately drops it from the stack
```
#### PULL REQUEST
* A request for another developer to pull a branch from my repo into their repo
* Pull request is a mechanism for developer to notify other teammembers that a feature **(worked on in a non-master branch)** is completed
* Pull requests lets to discuss the proposed feature
* Inside pull request, activity such as feedback and follow-up commits, is tracked
* When feature is accepted by project maintainer, it is merged in official repo and pull request is closed

#### GIT USING BRANCHES
##### GIT BRANCCH
* Independent line of development
* To encapsulate any changes, new work is done in a new branch, so unstable branch is never commited to a master branch
* Branches are just pointers to commits

* List all branches in my repo:

```
git branch
```
* Create a new branch:

```
git branch <new branch name>
```
* delete branch, but it prevents deleting branch with unmerged changes:

```
git branch -d <branch name> 
```
* Force delete branch:

```
git branch -D <branch name>
```
* Rename branch:

```
git branch -m <new branch name>
```
##### GIT CHECKOUT
* Navigates:
  * Between files
  * Between commits
  * Between branches
* **Checking out a commit** makes entire working directory mach the commit, use it to view old state of project without altering the current state
* **Checking out a file** lets you see an old version of that particular file, and leaves the rest of your vorking directory untouched
* **Checking out a branch** updates the files in the working directory to mach the version stored in that branch and it tells git to record all new commits to that branch
* `git checkout` selects which line of development you want to work on

* Make existing branch the current branch and updates the working directory to mach it:

```
git checkout <existing branch name>
```
* Make new branch based off current branch and then checkout it:

```
git checkout -b <new branch name>
```
* Make new branch based off `<existing branch name>` and then checkout it:

```
git checkout -b <new-branch> <existing branch name>
```
* Development should always take place in a branch never on a `detached HEAD` state

##### GIT MERGE
* Target branch (branch that is merged in another branch(?))remains unaffected by merge
* Takes independent lines of development created by `git branch` and integrates them in a single branch (current branch):

```
git merge
```
* To merge `<branch>` into current branch:

```
git merge <branch>
```
* To merge `<branch>` into current branch, and also generate a merge commit:

```
git merge --no-ff <branch>
```
#### UNDOING CHANGES

* Check the previous version of a file:

```
git checkout <commit> <file> #changes can now be undone by add and commit
```
* Generate a new commit that undoes all the changes introduced in ``<commit>`, and then apply that to current branch:
* Use this to remove an entire commit from project history:
* Only undoes a single commit, without reverting back to the previous project state:

```
git revert <commit>
# This reverts the commit that was just created:
git revert HEAD
```
##### GIT RESET

* Undo changes made in the most current commit, leave working directory unchanged:

```
git reset <commit> 
```
* Remove file from staging area, leave working directory unchanged:

```
git reset <file>
```




