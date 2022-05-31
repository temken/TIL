# Add commits to a pull-request from another user's fork

1. Add the fork to the remote.

```bash
git remote add other_user git@github.com:other_user/repo.git
```

Check via ```git remote -v``` if it worked.

2. Fetch from the remote.

```
git fetch other_user
```

3. Check out their branch locally, e.g. if it is the main rename_branch

```bash
git checkout -b other_user-main other_user/main
```

4. Commit your changes the usual way.

5. Push to the other user's remote's head.

```bash
git push other_user HEAD:main
```

(If you get an error here (```permission denied```), the other user might not have checked the ```Allow edits from maintainers``` option in the PR.)

## Source
[https://tighten.com/blog/adding-commits-to-a-pull-request/](https://tighten.com/blog/adding-commits-to-a-pull-request/)
