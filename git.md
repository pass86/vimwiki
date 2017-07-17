# archive latest
* git archive -o latest.zip HEAD

# server repo
* sudo mkdir /repo
* sudo git init --bare /repo/foo
* sudo chown -R user:user /repo/foo
* git clone user@server:/repo/foo
* git push --set-upstream origin master

# remove untracked
* git clean -dfx

# last version
* git diff HEAD^ HEAD

# change most recent commit message after push
* git commit --amend
* git push --force

# remove submodule
* git submodule deinit foo
* git rm foo

# color diff
* git config color.ui true

# undo add before commit
* git reset

# fix old mode 100755
* git config core.filemode false