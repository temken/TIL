# Fix up a recent git commit

Let's say we have this recent git history

```bash
git log -n 3 --oneline
c55d261 commit 3
302a557 commit 2
b8c0354 commit 1
```

And we notice a little error in ```commit 2``` that we want to quickly fix, but without necessarily add a 4th commit.

Then we can commit the new code using ```-fixup```

```bash
git commit --fixup 302a557
```

This will create a new commit:

```bash
git log -n 4 --oneline
97ffc93 fixup! commit 2
c55d261 commit 3
302a557 commit 2
b8c0354 commit 1
```

Finally it is possible to merge this new commit into commit 2 with ```-autosquash```.

```bash
git rebase -i --autosquash <branch>
```

or

```bash
git rebase -i --autosquash HEAD~4
```
or

```bash
git rebase --i --autosquash b8c0354
```

| :exclamation:  Here, the used commit is the last commit you want to leave unchanged, and *not* the commit you want to fix.   |
|-----------------------------------------|



We can also activate autosquashing by default: 

```bash
git config --global rebase.autosquash true
````

Since you changed the git history you might have to force-push the changed commits to your remote repository, if you have already pushed them.

```bash
git push -f origin <branch>
```

## Source
[https://fle.github.io/git-tip-keep-your-branch-clean-with-fixup-and-autosquash.html](https://fle.github.io/git-tip-keep-your-branch-clean-with-fixup-and-autosquash.html)
