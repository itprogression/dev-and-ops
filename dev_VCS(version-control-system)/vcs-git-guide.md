# Git 101

## Configure git

```
git config --global user.email "email_account@domain.com"
git config --global user.name "Name Lastname"
git config --global core.editor "vim"
```

### Advence: Signing commits

    * From the list of GPG keys, copy the long form of the GPG key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:

```
gpg --list-secret-keys --keyid-format=long
/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot
ssb   4096R/42B317FD4BA89E7A 2016-03-10

```

    * To configure your Git client to sign commits by default for a local repository, in Git versions 2.0.0 and above, run:

```
 git config commit.gpgsign true
 git config --global user.signingkey 3AA5C34371567BD2

```

    * To sign all commits by default in any local repository on your computer, run:

```
 git config --global commit.gpgsign true
 git config --global user.signingkey 3AA5C34371567BD2

```

### Advance: Configure Meld as difftool and mergetool for GIT

Source:
 - https://www.delftstack.com/es/howto/git/git-diff-meld/


#### For Windows users, run these commands

```
git config --global diff.tool meld
git config --global difftool.meld.path "C:\Program Files (x86)\Meld\Meld.exe"
git config --global difftool.prompt false

git config --global merge.tool meld
git config --global mergetool.meld.path "C:\Program Files (x86)\Meld\Meld.exe"
git config --global mergetool.prompt false

```

#### For linux/mac users, run these commands

```
git config --global diff.tool meld
git config --global difftool.meld.path "/usr/bin/meld"
git config --global difftool.prompt false

git config --global merge.tool meld
git config --global mergetool.meld.path "/usr/bin/meld"
git config --global mergetool.prompt false

```

## Genesis of GIT

### The Three States
    - States:
      - Git has three main states that your files can reside in:
        - Working Area:
          - modified
        - Staging Area:
          - staged
        - Repository (.git directory)
          - committed

### Create a remote repo:

Source:
 - https://docs.github.com/en/get-started/quickstart/create-a-repo

### Create a local repo:

  * Initialize the local directory as a Git repository.

```
git init -b main
```

  * Add the files in your new local repository. This stages them for the first commit.

```
git add .
```

  * Commit the files that you've staged in your local repository.

```
git commit -S -m "First commit"
```

### Connect a local repository with a remote repository

```
git remote add origin  <REMOTE_URL>
```

### Push the changes in your local repository to GitHub.com.

* A branch that already exists remotely
```
git push -u origin main
```

* A new branch in local, which does not exist in remote
```
git push --set-upstream origin newBranch
```

## Ordering the flow with GIT (Git flow vs GitHub flow)

### Git flow: Branch names, for all-in-one projects (docu, test, app)
    - Main branch:
      - Production branch: main
      - Develop branch: develop
      - Testing branch: test
      - Documentation branch: docu
    - Sub branch:
      - Feature prefix: feature/
      - Release prefix: release/
      - Hotfix prefix: hotfix/

### GitHub flow: Branch names, for simple projects
    - Main branch:
      - main
    - Subs branchs:
      - task/*
      - feature/*
      - bugfix/*
      - hotfix/*

## microMAN git

git-branch
 - List, create, or delete branches
 - https://git-scm.com/docs/git-branch

git-switch
 - Switch branches
 - https://git-scm.com/docs/git-switch

git-stash
 - Stash the changes in a dirty working directory away
 - https://git-scm.com/docs/git-stash

git-checkout
 - Switch branches or restore working tree files
 - https://git-scm.com/docs/git-checkout

## Fast GIT

### Always have to be sure of where you stand:

* To retrieve only the name of the branch you are on:

```
git branch --show-current
```

* Switch branch using git checkout

```
git checkout <existing_branch>
git checkout -b <new_branch>
```

* Switch branch using git switch

```
git switch <existing_branch>
git switch --create <new_branch>
```

* Bring to your local, the latest changes from the remote repo

```
git branch --set-upstream-to=origin/<existing_branch>
git pull
```

### Always keep track of your changes:

* Find modified files

```
git diff --name-only
git status
```

#### Move a file from: modified to staged (git add)

* One file:

```
git add path/filename
```

* All files:

```
git add .
git add -A
```

#### How to remove file from staged (undo git add...)

* Undo git add using restore

```
git restore --staged <filename>
```

* Undo it add using reset

```
git reset -- <filename>
git reset HEAD <filename>
```

* Erasing your local changes using git checkout
    - If we want to remove the modifications done to this file, we execute the command described:

```
git checkout -- <filename>
```

#### Record your changes:

* git commit -m
  * -m <msg> or --message=<msg>:
    * Use the given <msg> as the commit message. If multiple -m options are given, their values are concatenated as separate paragraphs.

```
git commit -m "msg"
git commit --message=<msg>"

```

* Create a signed commit: git commit -S -m
  * -s / --signoff / --no-signoff:
    * Add a Signed-off-by trailer by the committer at the end of the commit log message. The meaning of a signoff depends on the project to which you’re committing. For example, it may certify that the committer has the rights to submit the work under the project’s license or agrees to some contributor representation, such as a Developer Certificate of Origin.
  - https://docs.github.com/en/github/authenticating-to-github/managing-commit-signature-verification/telling-git-about-your-signing-key

```
git commit -S -m "your commit message"

```

#### Share your code:

* git push
  - https://git-scm.com/docs/git-push

```
git push origin <existing_branch>
```

## Advance git:

### Merge: B (new-feature) to A (master)

```
git checkout master
git pull
git branch new-feature
git checkout new-feature
git add filenameWithChanges
git commit -S -m "merge commit msg"
git checkout master
git pull
git merge new-feature

```

#### Start:

 /A1-A2-A3
X
 \B1-B2-B3


#### B to A with a merge commit:

 /A1-A2-A3-B*(1,2,3)
X
 \B1-B2-B3

### delete branch
* locally *
```
git branch -d localBranchName
git branch -d 638-opendistro-documentation

```

* remotely *
```
git push origin --delete remoteBranchName

```

### Create, list, delete or verify a tag object signed with GPG
 - https://git-scm.com/docs/git-tag

#### Creando una etiqueta ligera (lightweight)
```
git tag <tagName>

```

#### Creando una etiqueta anotada (annotated)
```
git tag -a <tagName> -m "tag msg"

```
### Stash the changes in a dirty working directory away
  - https://git-scm.com/docs/git-stash

  * stash save

```
git stash save --include-untracked "msg"
git stash save "changes for quick fix in 4.2"
```

  * list [< log-options >]
    * List the stash entries that you currently have. Each stash entry is listed with its name (e.g. stash@{0} is the latest entry, stash@{1} is the one before, etc.)

```
git stash list
```

  * show [-u|--include-untracked|--only-untracked] [<diff-options>] [<stash>]
    * Show the changes recorded in the stash entry as a diff between the stashed contents and the commit back when the stash entry was first created.

```
git stash show stash@{0}
```

  * apply [--index] [-q|--quiet] [<stash>]
    * Like pop, but do not remove the state from the stash list.

```
git stash apply stash@{0}
```

  * drop [-q|--quiet] [<stash>]
    * Remove a single stash entry from the list of stash entries.

```
git stash drop stash@{1}
```
