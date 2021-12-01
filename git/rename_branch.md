# Rename a branch
First rename the branch on github directly.

Then change the name on the local clones.

```bash
git branch -m master main
git fetch origin
git branch -u origin/main main
git remote set-head origin -a
git remote prune origin
```
 (Last one is optional, see link below.)

## Source

[Github documentation](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/renaming-a-branch)