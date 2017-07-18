# archive latest
```sh
git archive -o latest.zip HEAD
```

# server repo
```sh
sudo mkdir /repo
sudo git init --bare /repo/foo
sudo chown -R user:user /repo/foo
git clone user@server:/repo/foo
git push --set-upstream origin master
```

# remove untracked
```sh
git clean -dfx
```

# last version
```sh
git diff HEAD^ HEAD
```

# change most recent commit message after push
```sh
git commit --amend
git push --force
```

# remove submodule
```sh
git submodule deinit foo
git rm foo
```

# color diff
```sh
git config color.ui true
```

# undo add before commit
```sh
git reset
```

# fix old mode 100755
```sh
git config core.filemode false
```
