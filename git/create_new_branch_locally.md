# Create a new branch locally and push it to a remote server

First create a new branch of your local repository and switch to it.

```bash
git checkout -b <branch>
```

Do your code changes and commits.
Then, push it with the *-u* flag for *--set_upstream*.

```bash
git push -u origin <branch>
```


## Source

[Stack overflow](https://stackoverflow.com/questions/2765421/how-do-i-push-a-new-local-branch-to-a-remote-git-repository-and-track-it-too)