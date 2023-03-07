# Commands for Git and GitHub / GitLab

## Status etc.

| Description | Command | Comment |
| :---------- | :------ | :------ |

- git log
- Head

## Staging Area

| Description                                                | Command                   | Comment |
| :--------------------------------------------------------- | :------------------------ | :------ |
| Show status of the staging area                            | `$ git status`            |         |
| List all files in the staging area                         | `$ git ls-files`          |         |
| Add all changed files to the staging area                  | `$ git add .`             |         |
| Add the files "f1.txt" and "f2.txt" to the staging area    | `$ git add f1.txt f2.txt` |         |
| Remove all changed files from the staging area             | `$ git rm .`              |         |
| Remove the files "f1.txt" and "f2.txt" to the staging area | `$ git rm f1.txt f2.txt`  |         |

- add some changes
- add all changes
- remove some files
- remove all files

## Commits

| Description                          | Command                            | Comment          |
| :----------------------------------- | :--------------------------------- | :--------------- |
| List all commits                     | `$ git log`                        | exit log via `q` |
| Commit changes with a commit message | `$ git commit -m "commit message"` |                  |

| Remove untracked changes from "f1.txt" | `$ git checkout f1.txt` | checkout the latest commit of "f1.txt" |
| Remove all untracked changes | `$ git checkout .` | checkout the latest commit of all files |
| Remove all untracked changes | `$ git restore .` | checkout the latest commit of all files |
| Reset (soft) the head by 1 commit | `git reset --soft HEAD~1` | keep changes in the staging area |
| Reset the head by 1 commit | `git reset HEAD~1` | remove (i) the latest commit and (ii) clear the staging area |
| Reset (hard) the head by 1 commit | `git reset --hard HEAD~1` | remove (i) the latest commit, (ii) clear the staging area, and (iii) remove uncommitted file changes |
| List all untracked files | `$ git clean -dn` | listed files would be deleted upon `$ git clean -df` |
| Delete all untracked files | `$ git clean -df` | first, check for untracked files via `$ git clean -dn` |
| Go to a previous commit with ID `commitID` | `$ git checkout commitID` |
| Create a branch `myBranch` | `$ git branch myBranch` |
| Merge `myBranch` into `main` | `$ git merge myBranch ` | while on `main` |
| Create and change to a new branch `myBranch2` | `$ git checkout -b myBranch2` | `$ git switch -b myBranch2` is equivalent |
| List all local branches | `$ git branch` |
| Go to the `main` branch | `$ git checkout main ` | the latest commit of the current branch is the `HEAD` |
| Checkout the specific commit `56afce` | `$ git checkout 56afce` | commit `56afce` has to be on the current branch |

## Branches

| Description | Command | Comment |
| :---------- | :------ | :------ |

- create a local branch
- create a remote branch
- create a local tracking branch

## Heap

| Description | Command | Comment |
| :---------- | :------ | :------ |

## Stash

| Description | Command | Comment |
| :---------- | :------ | :------ |

## Pull requests

| Description | Command | Comment |
| :---------- | :------ | :------ |

## Extra 1: other useful shell commands

| Description                                              | Command                                 |
| :------------------------------------------------------- | :-------------------------------------- |
| Space ` ` for file names etc.                            | `$ \_`                                  |
| Present working directory                                | `$ pwd`                                 |
| List files in current folder                             | `$ ls`                                  |
| List files in folder `abc/xyz`                           | `$ ls abc/xyz`                          |
| Create empty / update files `f1.txt`and `f2.txt`         | `$ touch f1.txt f2.txt`                 |
| Create new folders `folder1` and `folder2`               | `$ mkdir folder1 folder2`               |
| Navigate into `path/to/folder`                           | `$ cd path/to/folder`                   |
| Go to the home directory                                 | `$ cd ~`                                |
| Go to the root directory                                 | `$ cd \`                                |
| Move files from `origin`to `destination`                 | `$ mv origin destination`               |
| Remove a folder `folder`                                 | `$ rm -r folder`                        |
| Copy a file from `origin/f1.txt` to `destination/f1.txt` | `$ cp origin/f1.txt destination/f1.txt` |
| Copy a folder from `origin` to `destination`             | `$ cp -r origin destination`            |
|                                                          |                                         |

## Extra 2: useful links

- https://git-scm.com/ (git)
- https://github.com/ (Github)
