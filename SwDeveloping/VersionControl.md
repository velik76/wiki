# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Push and delete remote branches](#push-and-delete-remote-branches)
  - [Sort branches by commit date](#sort-branches-by-commit-date)
  - [Undo last commit](#undo-last-commit)
  - [Remove single file from modified list (staging area)](#remove-single-file-from-modified-list-staging-area)
  - [Clean untracked files](#clean-untracked-files)
  - [Correct way to change Active Branch in a bare repository?](#correct-way-to-change-active-branch-in-a-bare-repository)
  - [Rebasing](#rebasing)
  - [Push all remote branches to other remote host](#push-all-remote-branches-to-other-remote-host)
  - [Change first commit](#change-first-commit)
  - [10 Tips to Push Your Git Skills to the Next Level](#10-tips-to-push-your-git-skills-to-the-next-level)


## Push and delete remote branches

So lets say you have checked out a new branch, committed some awesome changes, but now you need to share this branch though with another developer. You can push the branch up to a remote very simply:

```shell
git push origin newfeature
```

Where origin is your remote name and newfeature is the name of the branch you want to push up. This is by far the easiest way, but theres another way if you want a different option. Geoff Lane has created a great tutorial which goes over how to push a ref to a remote repository, fetch any updates, and then start tracking the branch.

Deleting is also a pretty simple task (despite it feeling a bit kludgy): 

```shell
git push origin :newfeature
```

That will delete the newfeature branch on the origin remote, but youll still need to delete the branch locally with git branch -d (-D) feature

## Sort branches by commit date

```shell
git for-each-ref --sort=-committerdate refs/heads
```

## Undo last commit

```shell
git reset --soft HEAD~1
```

## Remove single file from modified list (staging area)

```shell
git reset HEAD -- <file>
```

## Clean untracked files

```shell
git clean -f -d
```

## Correct way to change Active Branch in a bare repository?

**Problem**
I have a bare repository that's used as the central store for my project. All the developers do "git clone " to share with it. When they do the clone, they get a checkout of the master branch (unless they do "git clone -n") because repo.git/HEAD contains "ref: refs/heads/master", making this the Active Branch.

**Solution**
If you have access to the remote bare repo, this article suggests:

```shell
git symbolic-ref HEAD refs/heads/mybranch
```

Which will update the HEAD file in your repository so that it contains:

```shell
ref: refs/heads/mybranch
```

## Rebasing

How is to rebase my developing state placed on (for example) linux kernel 3.3.8 on the linux kernel 3.7? Use for this rebase --onto command. Something like this:

```shell
git rebase --onto linux-3.7 linux-3.3.8 linux-3.3.8_with_patches
```

Additional discussion about this problem stored in [Link](http://www.linux.org.ru/forum/development/8587400?lastmod=1356074629996#comment-8616394)

## Push all remote branches to other remote host

If we have

**korg**
**rorg**

remotes we can push all branches from korg to rorg via:

```shell
git push rorg refs/remotes/korg/*:refs/heads/*
```

see [Link](http://stackoverflow.com/questions/7818927/git-push-branch-from-one-remote-to-another)

## Change first commit

```shell
git rebase -i --root
```

## 10 Tips to Push Your Git Skills to the Next Level

[Link](http://www.sitepoint.com/10-tips-git-next-level/)
