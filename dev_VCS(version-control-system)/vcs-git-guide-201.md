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

