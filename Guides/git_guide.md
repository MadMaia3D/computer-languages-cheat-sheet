# Git

## User Setup

To set the user information:

```
git config --global user.name "Your Name"
git config --global user.email <yourEmail@email.com>
```

To get the user information:

```
git config user.name
git config user.email
```

---

## Repository Initialization and information

To create a repository in the current directory:

```
git status
```

To get the current status of the repository:

```
git init
```

---

## Staging Changes

To add one or more files to the stage area:

```
git add <file_path>
git add <file_path_1> <file_path_2>
```

Add all new or changed files to the stage area:

```
git add .
```

---

## Commiting Changes

Commit the staged changes (will open configured text editor to edit the commit message):

```
git commit
```

Use the -m parameter to commit the staged changes with a message:

```
git commit -m 'message'
git commit -m "message"
```

Use the -a parameter to automatically add changed files and commit. This include ONLY the tracked files that have changed, not untracked files. These you will have to add manually.

```
git commit -a
```

The --amend parameter allow you to make changes to your last commit, either changing the message and/or including files you forgot to include. Ammending will include any staged files (if there is any) to the last commit.

```
git commit --amend
```

You still can use the -m parameter to write the message directly in the terminal:

```
git commit --amend -m "New commit message"
```

Use the --no-edit to amend without changing the message:

```
git commit --amend --no-edit`
```

---

## To Log Commits

Show a history of the commits of the branch:

```
git log
```

Use the --oneline parameter to see a simplified version of the log:

```
git log --oneline
```

---

## Working with Branches

Branches are like alternate time lines for you project.  
To view all branches:

```
git branch
```

## Creating branches:

Create a branch without switching to it (the name shouldn't include spaces):

```
git branch <branch-name>
```

## Switching branches:

To switch branch:

```
git switch <branch-name>
```

> Checkout is also used to change the HEAD to any commit

Create a branch and switch to it:

```
git switch --create <branch-name>
git switch -c <branch-name>
```

## Old Switching Commands:

The checkout command had many uses, including changing branches. Before the switch command was created, this was the way to travel between them.

Old command for switching:

```
git checkout <branch-name>
```

Old command for creating a branch and switching to it:

```
git checkout -b <branch-name>
```

## Delete and Rename Branches:

Delete branches that are already merged (HEAD should not be at the branch):

```
git branch --delete <branch-name>
git branch -d <branch-name>
```

Delete branches that are not merged (HEAD should not be at the branch):

```
git branch --delete --force <branch-name>
git branch -d -f <branch-name>
git branch -D <branch-name>
```

Rename/move CURRENT branch:

```
git branch --move <branch-name>
git branch -m <branch-name>
```

## Merging Branches:

To merge switch to the destination branch, where the changes should be integrated to, and use the merge command.  
To merge, switch to the branch that will get the changes and use the merge command passing it the branch that will be the source. In other words, the current branch will get the work done on the specified branch:

```
git merge <branch-name>
```

> Fast-Forward merge it's the simplest merge of all. It happens when the parent branch didn't changed.
>
> When the destination branch has changed since the creation of the source branch, a Fast-Forward Merge isn't possible.
>
> What happens is that git creates a Merge Commit.

Using the verbose option, git branch show the commit that each branch points to:

```
git branch --verbose
git branch -vv
git branch -v
```

---

## Comparing Changes With The Diff Command

Use git diff to compare the staging area and working directory.
Basically shows what changed since the last commit and it is NOT staged.

```
git diff
```

Use git diff HEAD to list all the changes in the working directory since the last commit.
Basically shows what changed since the last commit.

```
git diff HEAD
```

To list the changes between the staging area and the last commit, use one of the following commands:

```
git diff --staged
git diff --cached
```

You can specify just one file in the previous commands:

```
git diff <file-name>
git diff HEAD <file-name>
git diff --staged <file-name>
git diff --cached <file-1-name> <file-2-name>...<file-n-name>
```

Between two branches:

```
git diff branch1..branch2
git diff branch1 branch2
```

Between two commits:

```
git diff commit1..commit2
git diff commit1 commit2
```

---

## Stashing (Needs more information)

Stashing allows you to save changes to recover later.

Save commited changes, staged or unstaged, and hide it:

```
git stash save
```

Use stash pop to get the back the last staged changes:

```
git stash pop
```

Stash apply retrieves what is in the stash without removing it from the stash:

```
git stash apply
```

> Basically makes a copy from what is in the stash. Can generate conflicts.  
> Useful to apply the same changes in multiple branches.

## Working with multiple stashes (Needs more information):

You have a stack of stashes. You will always pop the last changes that you added.  
You can view all stashes at each commit:

```
git stash list
```

To apply a particular stash:

```
git stash apply stash@{number_of_stash}
```

To drop a particular stash:

```
git stash drop stash@{number_of_stash}
```

To drop everything in the stash:

```
git stash clear
```

---

## Undoing Changes & Time Traveling

## Travel between commits:

View a previous commit:

```
git checkout <commit-hash>
```

> To re-attach the head to a branch, just switch to a branch using switch or checkout.

HEAD^ or HEAD~1 refers to the commit before HEAD (parent), think of it as HEAD minus 1.  
HEAD^^ or HEAD~2 refers to 2 commits before HEAD (grandparent), think of it as HEAD minus 2.

```
git checkout HEAD^^^
git checkout HEAD~3
```

> Can be used many times in a row, like a HEAD position undo.

Use a dash (-) to switch to previous active branch or detached HEAD.

```
git switch -
git checkout -
```

## Undoing changes in the working area:

You can use the staged option to unstage a file:

```
git restore --staged <file-name>
```

To discard changes since the last commit:

```
git checkout HEAD <file-names>
git checkout -- <file-names>
git restore <file-names>
```

You can use restore to get any prior version of a file using the source option:

```
git restore --source <commit-reference> <file-name>
example:
git restore --source HEAD~2 my_file_1.txt my_file_2.txt
```

## Undoing Commits

Git can reset the repo back to a specific commit. This will remove commits that came after, but the changes will continue in the working area (the files will continue the same), so you can commit these again if you want.

```
git reset <commit-hash>
```

If you want to remove the commits without keeping the changes to the working directory, you have to use the hard option. This is similar to using the default reset and then using the restore command with the same commit.

```
git reset --hard <commit-hash>
```

> Git reset actually moves the branch pointer backwards, eliminating commits as if they existed.

You can create a new commit that undoes a previous single commit. It's basically a negative/inverse of the targeted commit.

```
git revert <commit-hash>
```

> git revert can result in conflicts too.

---

## GitHub/ Remote Repositories

The commands in this section have the purporse of interractiong with remote repositories:

View git remotes of the repo:

```
git remote -v
```

To add a remote:

```
git remote add <remote-name> <url>
```

> The convention for the name is "origin". The url can be of any remote repository, for example, one from GitHub.

To change remote url:

```
git remote set-url <remote-name><url>
```

If you want to rename or remove a remote (not common):

```
git remote rename <old-name> <new-name>
git remote remove <remote-name>
```

To push to the remote repo:

```
git push <remote-name> <branch>
```

To push to a branch of different name on the remote repo (not recommended):

```
git push <remote-name> <local-branch>:<remote-branch>
```

Setting a push upstream, enables us a shorter way of the push command:

```
git push -u <remote-name <branch>
git push -u <remote-name <local-branch>:<remote-branch> (not recommended)
git push
```

> After you push using the upstream '-u' options, you can just use git push to push the changes to the remote repository.
