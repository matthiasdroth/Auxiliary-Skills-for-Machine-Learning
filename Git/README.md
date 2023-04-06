# Git Commands Cheat Sheet

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

## Commits

| Description                                      | Command                                             | Comment                                         |
| :----------------------------------------------- | :-------------------------------------------------- | :---------------------------------------------- |
| List all commits                                 | `$ git log`                                         | exit log via `q`                                |
| Commit changes with a commit message             | `$ git commit -m "commit message"`                  |                                                 |
| Remove a commit (soft)                           | `$ git reset --soft HEAD~1`                         | remove the last n=1 commits                     |
| Remove a commit                                  | `$ git reset HEAD~1`                                | also remove changed files from the staging area |
| Remove a commit (hard)                           | `$ git reset --hard HEAD~1`                         | also remove changes to files                    |
| push local changes to remote                     | `$ git push`                                        | this requires an upstream branch                |
| set up upstream branch `myBranch` and push to it | `$ git push --set-upstream remotes/origin/myBranch` | this assumes `origin` to be a remote            |

## Stash

| Description                                              | Command                            | Comment                                                                                                      |
| :------------------------------------------------------- | :--------------------------------- | :----------------------------------------------------------------------------------------------------------- |
| Move uncommitted and unstaged changes to the stash       | `$ git stash`                      | the current branch has no changes anymore; `git stash` can be applied repeatedly, thus creating more stashes |
| Add a message to a new stash                             | `$ git stash push -m "my message"` | the pushed message is shown next to the stash when running `$ git stash list`                                |
| Inspect the stashes                                      | `git stash list`                   | the latest stash is always at the top and stash indices are shown                                            |
| Move changes from the latest stash to the current branch | `$ git stash apply`                | apply the latest stash                                                                                       |
| Move changes from the third stash to the current branch  | `$ git stash apply 3`              | apply the third stash                                                                                        |
| Move the latest (=> index 0) stash to our project        | `$ git stash pop 0`                | the according stash is deleted $\Rightarrow$ this can be run repeatedly                                      |
| Delete a specific stash via its index                    | `$ git stash drop 0`               |                                                                                                              |
| Delete the entire stash stack                            | `$ git stash clear`                |                                                                                                              |

## Reflog

The reflog (_referenc log_) stores all changes that we have made in our git project (but only for 30 days). For example, the reflog can restore changes on a feature branch that has been deleted.

| Description                                        | Command                      | Comment                                     |
| :------------------------------------------------- | :--------------------------- | :------------------------------------------ |
| List all changes (≤ 30 days) of the current branch | `$ git reflog`               | IDs, head indices, etc. are listed          |
| hard reset to a given ID (`1b3ec1a`)               | `$ git reset --hard 1b3ec1a` | detached HEAD $\Rightarrow$ create a branch |
| hard reset to a given head index (`3`)             | `$ git reset --hard HEAD~3`  | detached HEAD $\Rightarrow$ create a branch |

## Else

| Description                                   | Command                       | Comment                                                                                              |
| :-------------------------------------------- | :---------------------------- | :--------------------------------------------------------------------------------------------------- |
| show name of remote                           | `$ git remote`                |                                                                                                      |
| Remove untracked changes from "f1.txt"        | `$ git checkout f1.txt`       | checkout the latest commit of "f1.txt"                                                               |
| Remove all untracked changes                  | `$ git checkout .`            | checkout the latest commit of all files                                                              |
| Remove all untracked changes                  | `$ git restore .`             | checkout the latest commit of all files                                                              |
| Reset (soft) the head by 1 commit             | `git reset --soft HEAD~1`     | keep changes in the staging area                                                                     |
| Reset the head by 1 commit                    | `git reset HEAD~1`            | remove (i) the latest commit and (ii) clear the staging area                                         |
| Reset (hard) the head by 1 commit             | `git reset --hard HEAD~1`     | remove (i) the latest commit, (ii) clear the staging area, and (iii) remove uncommitted file changes |
| List all untracked files                      | `$ git clean -dn`             | listed files would be deleted upon `$ git clean -df`                                                 |
| Delete all untracked files                    | `$ git clean -df`             | first, check for untracked files via `$ git clean -dn`                                               |
| Go to a previous commit with ID `commitID`    | `$ git checkout commitID`     |
| Create a branch `myBranch`                    | `$ git branch myBranch`       |
| Merge `myBranch` into `main`                  | `$ git merge myBranch `       | while on `main`                                                                                      |
| Create and change to a new branch `myBranch2` | `$ git checkout -b myBranch2` | `$ git switch -b myBranch2` is equivalent                                                            |
| List all local branches                       | `$ git branch`                |
| Go to the `main` branch                       | `$ git checkout main `        | the latest commit of the current branch is the `HEAD`                                                |
| Checkout the specific commit `56afce`         | `$ git checkout 56afce`       | commit `56afce` has to be on the current branch                                                      |

## Merging

| Description                                      | Command                            | Comment                                     |
| :----------------------------------------------- | :--------------------------------- | :------------------------------------------ |
| fast-forward merge _feature_ onto current branch | `$ git merge -ff feature`          | condition: no new commits on current branch |
| recursively merge _feature_ onto current branch  | `$ git merge -s recursive feature` |                                             |

Apart from `fast-forward` and `recursive` / `ort` (**o**stensibly **r**ecursive's **t**win) there are also the `resolve`, `octopus`, `ours`, and `subtree` strategies. See the [official documentation](https://git-scm.com/docs/git-merge) for further details.

## Branches

| Description                             | Command                    | Comment                                          |
| :-------------------------------------- | :------------------------- | :----------------------------------------------- |
| Delete the branch `xyz`                 | `$ git branch -d xyz`      |                                                  |
| Show information on the `origin` remote | `$ git remote show origin` |                                                  |
| List all branches                       | `$ git branch -a`          |                                                  |
| List remote branches                    | `$ git branch -r`          |                                                  |
| List information on local branches      | `$ git branch -vv`         | shows IDs, upstream branches and commit messages |
| Force deletion of branch `xyz`          | `$ git branch -D xyz`      | also works if `xyz` has not been merged, yet     |

- create a local branch
- create a remote branch
  | List remote branches | `$ git branch -r` | |
- create a local tracking branch

## Pull requests

| Description | Command | Comment |
| :---------- | :------ | :------ |

## Remotes

| Description                                                  | Command                           | Comment                                                     |
| :----------------------------------------------------------- | :-------------------------------- | :---------------------------------------------------------- |
| set `origin` as a remote for `url`                           | `$ git remote add origin url`     | `url` is the URL of the remote `origin`                     |
| clone repo with url `https://myUrl.com` from remote          | `$ git clone https://myUrl.com`   | clones the repo folder into the current directory           |
| clone repo with url `https://myUrl.com` from remote in place | `$ git clone https://myUrl.com .` | clones the repo folder _content_ into the current directory |

## Detached `HEAD`

| Description                          | Command                             | Comment                                                                                                |
| :----------------------------------- | :---------------------------------- | :----------------------------------------------------------------------------------------------------- |
| Directly checkout commit `f3c499`    | `$ git checkout f3c499`             | `$ git log` will show a detached `HEAD` $\Rightarrow$ the checked out commit is not part of any branch |
| Turn a detached `HEAD` into a branch | `$ git branch detached-head-branch` |                                                                                                        |

## Ignoring files via `.gitignore`

- Use a `.gitignore` file for specifying which files git should ignore.
- Large files can trigger usage limits and thus trigger `$ git push` to fail.
- Automatically generated files (e.g. `.eslintcache`) do not need to be tracked.
- A single `.gitignore` file in the root folder of the repo – next to the `.git` folder – is usually sufficient.
- Ignore a specific file by adding it to `.gitignore` in a separate line, e.g., `file1.txt`.
- Ignore all files of a specific file type by adding and entry with a `*` wildcard, e.g., `*.bin`.
- Make exceptions and do track files that would be ignored via `!`, e.g., `!important.bin`.
- Ignore the files in a specific subfolder via, e.g., `app/js/*`, where `js` is the subfolder.
- When in doubt, refer to the official [`.gitignore` documentation](https://git-scm.com/docs/gitignore).

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

## Extra 2: useful links

- https://git-scm.com/ (git)
- https://github.com/ (Github)

---

Open this file with your browser and use the browser's built-in print function to export the cheat sheet to PDF.
