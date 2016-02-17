GIT INSTRUCTIONS
================

#### GIT STAGING AREA:

* Buffer between working directory and project history
* Staging allows to group related changes before `commit`ing them to project history

#### GIT CONFIG:

```bash
git config --global user.name "name-surname"
```

#### CREATE NON BARE REPO IN WORKING DIRECTORY:

```bash
git init
git remote add <project_name or origin> <ssh or web address>
git clone <ssh or web address> #no real need for this, but it sets branch tracking automatically
```
--------------------------------
#### GITIGNORE:

* `touch .gitignore` -- *set up .gitignore*
* `cat .gitignore` -- *.gitignore contents*
* **gitignore wildcards:**
  * `<fodername>/` -- *will ignore any folder with foldername*
  * `*.<extension>` -- *ignores all files with this extension*
  * `<filename>` -- *ignores file with filename*
  * `<filename>*` -- *ignores filename with any extenson*

-----------------------
#### GIT ACTIONS:

* `git log --stat` -- *Shows log with filechanges*
* `git status` -- *show changes in project directory and staging area*
* `git rm --cached <file>` -- *removes unwanted **file** from staging area (shows up in git status)*
* `git rm -r --cached <file>` -- *removes unwanted **folder** from staging area (shows up in git status)*

* add needed changes to Index:

```
git add <filename>
git add -A #adds all files
git add -p #begins an interactive staging session
```

  * `git commit -m "Commit message"` -- *commit to local repo. Commits the staged snapshot*
  * `git commit -a -m "Commit message"` -- *commit to local repo. Allows to commit skipping git add step by adding everything in git status*

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

------------------
#### GIT USING BRANCHES

* Independent line of development
* To encapsulate any changes, new work is done in a new branch, so unstable branch is never commited to a master branch
* Branches are just pointers to commits
* **Master** branch is no special, its just the same as others and can be renamed
* **HEAD** is just a pointer to the current branch

  * `git branch` -- *List all branches in my repo*
  * `git branch -a` -- *list all branches*
  * `git branch <new branch name>` -- *Create a new branch*
  * `git branch -d <branch name>` -- *delete branch, but it prevents deleting branch with unmerged changes*
  * `git branch -D <branch name>` -- *Force delete branch*
  * `git branch -m <new branch name>` -- *Rename branch*
  * `git branch -v` -- *shows last commits on each branch*

-------------------------
##### LOCAL BRANCH

* branch that is on my local repo
* local branch can and mostly should be set to track a remote branch (not necessarily the same name)
* `Tracking branches` are local branches that have a direct relationship to a remote branch.
  * `git branch -vv` -- *shows upstream info for all local branches*
  
-------------------------
##### REMOTE BRANCH


-------------------------
#### GIT CHECKOUT
* Navigates:
  * Between files
  * Between commits
  * Between branches
* **Checking out a commit** makes entire working directory mach the commit, use it to view old state of project without altering the current state
* **Checking out a file** lets you see an old version of that particular file, and leaves the rest of your vorking directory untouched
* **Checking out a branch** updates the files in the working directory to mach the version stored in that branch and it tells git to record all new commits to that branch

  * `git checkout` -- *selects which line of development you want to work on*
  * `git checkout <existing branch name>` -- * Make existing branch the current branch and updates the working directory to mach it*
  * `git checkout -b <new branch name>` -- * Make new branch based off current branch and then checkout it *


* Make new branch based off `<existing branch name>` and then checkout it:

```
git checkout -b <new-branch> <existing branch name>
```
* Development should always take place in a branch **never** on a `detached HEAD` state

----------------------
#### GIT MERGE
* Target branch (branch that is merged in another branch(?))remains unaffected by merge
* `git merge` -- *Takes independent lines of development created by `git branch` and integrates them in a single branch (current branch)*
* `git merge <branch>` -- *To merge `<branch>` into current branch*
* `git merge --no-ff <branch>` -- *To merge `<branch>` into current branch, and also generate a merge commit*
* after merging, delete the unneeded branch
* `git branch -d <branchname>` -- deletes branch

------------------------
#### MERGE CONFLICTS
* arises when there is a change on the same part of the same file on two branches being merged
* run `git status` to see which files are **unmerged**, open them and merge manually
* run `git add` on each file to mark it as resolved, then do `git commit`


---------------------
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

* `git reset <commit>` -- *Undo changes made in the most current commit, leave working directory unchanged*
* `git reset <file>`   -- *Remove file from staging area, leave working directory unchanged*

##### GIT AMEND

* `git commit --amend` -- *takes your staging area and uses it for the commit. If you’ve made no changes since your last commit (for instance, you run this command immediately after your previous commit), then your snapshot will look exactly the same, and all you’ll change is commit message*

* example workflow: (second commit replaces the first commit):

```bash
git commit -m 'initial commit'
git add <forgotten_file>
git commit --amend
```

-----
#### GIT FETCH VS GIT PULL

* Locally, a local repo and a copy of remote repo is stored
* 'git fetch'  brings local copy of remote repo up to date, this never changes any of my own local branches, so it **does not change my working copy**
* 'git pull' brings the remote repo changes in local repo, where I keep my code, so it **changes my working copy**
* Normally, 'git pull' first does 'git fetch' adn then merges 'git merge' changes in my local code repo.

-------
#### WORKING WITH REMOTE REPOS

* `git remote` -- *shows configured remote repos*
* `git remote -v` -- *shows all remote repos with urls*
* `git remote add <name> <url>` -- *adds new remote repo*
* `git push <remote repo name> <remote repo branch>`
* `git remote show <remote repo name>` -- *shows info about remote repo*

--------------
#### GIT TAGGING

* git allows to **tag** specific points in history as being important
* `git tag` -- *shows all existing tags*
* *lightweiht tag* is a pointer to specific commit
* *annotated tag* is a full object in git database
* `git tag -a <tagname> -m "message"` -- *create a new **annotated**tag*
* `git tag <tagname>` -- *create a new **lightweiht** tag*
* `git show <tagname>` -- *shows tag info*
* it is also possible to tag past commits
* `git push` doses not transfer tag info by default
  * `git push <remote repo name>  <tagname>` -- *pushes tags to remote repo*
  * *cloning* and *pulling* does transfer tag info

---------------
#### MERGE CONFLICT 

* Resolve conflict between two branches like this:
```
git checkout master
git pull
git checkout <branch>
git merge master
# manually resolve conflicts
git add
git commit
git push
```
