# revert last commit
```sh
git revert HEAD
```

# delete the most recent commit
```sh
git reset --hard HEAD~1
```

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

# add submodule
```sh
git submodule add https://github.com/foo/bar.git external/bar
```

# remove submodule
```sh
git submodule deinit foo
git rm foo
```

# Fix 'Unable to find current origin/master revision in submodule path ...'
```sh
git submodule set-branch --branch main foo_path
```

# Init submodule
```sh
git submodule update --init --recursive
```

# Update submodule
```sh
git submodule update --remote --recursive
```

# create bundle
```sh
git bundle create foo.bundle HEAD main
```

# clone bundle
```sh
git clone foo.bundle foo
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

# commit changes to new branch
```sh
git checkout -b foo
git commit -am"foo"
git push --set-upstream origin foo
```

# create branch
```sh
git checkout -b foo
git push origin foo
```

# switch back to master
```sh
git checkout master
```

# remote url
```sh
git remote -v
git remote set-url origin git@github.com:pass86/dotfiles.git
```

# rewriting the most recent commit message
```sh
git commit --amend
```

# lfs test server
```sh
git config -f .lfsconfig lfs.url http://localhost:9999
```

# fix SSL certificate problem: self signed certificate
```sh
git -c http.sslVerify=false clone https://foo.com/bar.git
cd bar
git config http.sslVerify false
```

# Fetch all tags
```sh
git fetch --all --tags
```

# List tags
```sh
git tag
```

# Checkout from tags
```sh
git checkout tags/foo -b dev-foo
```

# Convert large Git objects to LFS pointers
```sh
git lfs migrate import --include="foo.bin"
```
