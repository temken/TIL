# Undo the most recent git commit

In order to remove the most recent git commit you can run

```bash
git reset --soft HEAD~1
```

This rewinds the current HEAD branch to the revision *one before the current revision*. The **--soft** flag ensures that current changes are preserved. Using **--hard** instead will remove those changes.

Afterwards, the files changed by the now deleted commit are staged, and are unstaged via 

```bash
git reset
```

## Source
[https://www.git-tower.com/learn/git/faq/undo-last-commit](https://www.git-tower.com/learn/git/faq/undo-last-commit) 