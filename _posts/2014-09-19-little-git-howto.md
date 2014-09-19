---
layout: post
title: Little Git How To
permalink: little-git-howto
---

## Sync with Remote Repository
Show the relation of local branches to the remote branches:

```
git remote show origin
```

Load all data from remote origin into your local repository. Does not merge into your local branches. Its an update of your local storage of the remote branches. With -p (prune) it will remove branches from local repository, that are already removed in the remote repository:

```
git fetch -p origin
```

Remove branches from local repository, that are already removed in the remote repository:

```
git remote prune origin
```

Fetch and merge a remote branch into your local branch:

```
git pull
``` 

Push your changes to the remote repository:

```
git push origin <branch-name>
```

## Branches
List all branches:

```
git branch     # local branches only
git branch -a  # local and remote branches
git branch -v  # list includes last commit message
```

Create a branch and switch to it:

```
git checkout -b <branch-name>
```

Switch to a branch:

```
git checkout <branch-name>
```

Push a branch to the remote repository:

```
git push origin <branch-name>
```

Delete a local branch:

```
git branch -d <branch-name> # remove local merged branch
git branch -D <branch-name> # delete irrespective of merged status
git branch -r <branch-name> # delete also local origin branch
``` 

Delete a branch in the remote repository and in local origin:

```
git push origin :<branch-name>
```

Merge branch-1 into branch-2:

```
git checkout <branch-2>
git merge <branch-1>
```

## Undoing Things
Unstage a staged file:

```
git reset HEAD <file>
``` 

Discard all changes in a file and replace it with the last commit:

```
git checkout -- <filename>
```

###How to correct a merge into a wrong branch. 
Example: 
you merged via gitlab the feature branch feature/foo into master, but you wanted to merge it into develop. The feature branch was deleted by gitlab.

```
# find out the commit hash of the head from the 
# deleted feature branch and create a new feature 
# branch with this head

git branch feature/foo_b <commit_hash>

# find out the commit hash that was the head of master
# before you accidentally merged

git checkout master
git reset --hard <commit_hash of previous head of master>
push --force origin master
```

Now your accidentally merge into master is undone and you can merge your new created feature branch "feature/foo_b" into the right branch.

<font color='red'>
Warning:
Do not use "git reset --hard" and "push --force origin" if anybody in your team may have used your accidental merge commit as a parent commit. Then these commits are hanging around with no connection to a branch and you get a mess. This is history rewriting and should be used with care.
</font>

## Tags
List all tags:

```
git tag
```

Show most resent annotated tag:

```
git describe
```

Show detail info of tag <tagname>:

```
git show <tagname>
```

Create new annotated tag:

```
git tag -a <tagname> -m ’<commit message>’
```

Push tag to remote origin:

```
git push origin <tagname>  # only one tag	
git push origin --tags     # all tags
```

## Local Git Configuration

Change default editor:

```
git config --global core.editor vim
```

## Tools
A very nice inux (gnome) tool to display the tree structure of the commits and branches is gitg:

```
apt-get install gitg
```
