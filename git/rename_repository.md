# Rename a repository

A repository on github can easiest be renamed directly on the github webpage.

Afterwards, all local clones need to change their remotes. You can view them via

```bash
git remote -v
```

Change the remotes to the new url via

```bash
git remote set-url origin git@github.com:user/new_name.git
```

Here *origin* is the default remote.

## Source

[Github documentation](https://docs.github.com/en/repositories/creating-and-managing-repositories/renaming-a-repository)