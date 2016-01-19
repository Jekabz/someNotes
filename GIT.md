GIT INSTRUCTIONS
================

######GIT CONFIG:

```bash
git config --global user.name "name-surname"
```

######CREATE NON BARE REPO IN WORKING DIRECTORY:

```bash
git init
git remote add <project_name or origin> <ssh or web address>
git clone <ssh or web address> #no real need for this, but it sets branch tracking automatically
```
######GITIGNORE:

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
######GIT ACTIONS:

* show changes in project directory:

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
```

* commit to Head (not remote repo):

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
###### PULL REQUEST
* A request for another developer to pull a branch from my repo into their repo
* Pull request is a mechanism for developer to notify other teammembers that a feature **(worked on in a non-master branch)** is completed
* Pull requests lets to discuss the proposed feature
* Inside pull request, activity such as feedback and follow-up commits, is tracked
```
//todo
```

