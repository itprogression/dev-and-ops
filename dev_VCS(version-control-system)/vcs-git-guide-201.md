# Git 201

## Overwrite my local changes

*The scenario is the following. You are working in a local branch. You have committed changes, and uncommitted changes. Pulling the remote brings changes with a tricky and dangerous merge. You choose to LOSE the local changes.*

### How does all this work?

  - git fetch downloads the latest from remote without trying to merge or rebase anything
  - git reset resets the workingBranch branch to what you just fetched.
  - The --hard option changes all the files in your working tree to match the files in origin/master branch

```
 git checkout workingBranch
 git branch backup-badBranch-workingBranch
 git fetch --all
 git reset --hard origin/workingBranch
```

## How to Undo the Last Commit

### The revert command
The revert command will create a commit that reverts the changes of the commit being targeted. You can use it to revert the last commit like this:

```
 git revert <commit to revert>
```

### The reset command
You can also use the reset command to undo your last commit. But be careful – it will change the commit history, so you should use it rarely. It will move the HEAD, the working branch, to the indicated commit, and discard anything after:
The --soft option means that you will not lose the uncommitted changes you may have.

```
 git reset --soft HEAD~1
```

If you want to reset to the last commit and also remove all unstaged changes, you can use the --hard option:

```
 git reset --hard HEAD~1
```


