# Modify the most recent git commit

In order to modify the most recent, premature git commit you can use **git commit -amend**.

First **git add** all changes that should have been part of the recent commit, but were forgotten somehow.

Then run

```bash
git commit -amend
```

or

```bash
git commit --amend -m "updated commit message"
```

This combines staged changes with the recent commit. (It will actually replace the recent git commit with a completely new commit).

If the git message is fine the way it is, add the **--no-edit** flag at the end.

**Warning:** Be very careful, if the recent commit has already been pushed to e.g. github and you are working with collaborators. If you are working alone on a repository, it should be no problem. In that case you have to force push the 'new version' of the commit via 

```bash
git push -f
```

(If you amend and force-push a commit very shortly after the recent commit was pushed originally, it might confuse and break the CI test build.)

## Source
[https://www.atlassian.com/git/tutorials/rewriting-history](https://www.atlassian.com/git/tutorials/rewriting-history) 