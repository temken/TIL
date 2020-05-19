# Revert (and save) uncommitted changes

Local changes to files which have not been committed yet can be undone, both reversibly and irreversibly. 

## Whole repository

The most drastic (and irreversible) is to remove *all* local uncommited changes via
```bash
git reset --hard
```
Less drastic, you can undo all changes, but save them:
```bash
git stash
```
Changes saved in this way can be listed via
```bash
git stash list
```
and restored through
```bash
git stash pop
```
The can also be permanently deleted,
```bash
git stash clear
```
However, this deletes *all* stashed states. Running
```bash
git stash drop
```
only removes the latest state.

## Individual files

Permanently reseting a file to its latest commited version can be achieved by
```bash
git checkout -- <file>
```

*Note:* If the file has already been staged (but not commited), it needs to be unstaged before,
```bash
git reset HEAD <file>
```

## Source
[https://docs.gitlab.com/ee/topics/git/numerous_undo_possibilities_in_git/](https://docs.gitlab.com/ee/topics/git/numerous_undo_possibilities_in_git/)