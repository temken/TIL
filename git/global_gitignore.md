# Create a global, machine-specific .gitignore file for all repositories

Certain files in git repositories, which should not be tracked, are specific to the local machine (e.g. IDE or OS specific files).
It might not be desirable to list them in all repositories' *.gitignore* files.
Instead one can set up a global *.gitignore* file and tell your local git configuration about it.

Let's say we have created the file *~/.gitignore*. Then we can execute this command:

```bash
git config --global core.excludesfile ~/.gitignore
```

This will create the following entry in the *.gitconfig*:

```bash
[core]
    excludesfile = <home-dir>/.gitignore
```

From now on, no repository on that machine will try to track any of the files listed in *~/.gitignore*.

## Source

[Research Software Hour 003](https://researchsoftwarehour.github.io/2020/05/12/rsh-003.html)

[(link to video)](https://www.youtube.com/watch?v=RYYimW-Qj-4&list=PLpLblYHCzJAB6blBBa0O2BEYadVZV3JYf&index=4&t=1657s)