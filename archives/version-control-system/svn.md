# undo last checkin
```sh
svn merge -r HEAD:PREV path
```

# undo single revision
```sh
svn merge -c -rxxxx path
```

# revert to revision
```sh
svn merge -r HEAD:xxxx path
```

# up to revision
```sh
svn up -r xxxx path
```

# show log
```sh
svn log -l10 -v
svn log -rBASE -v
```

# show diff
```sh
svn log -rBASE --diff
```

# remove unversioned
```sh
svn cleanup . --remove-unversioned
```

# switch workingcopy
```sh
svn switch http://server/proj/branches/branch1 --ignore-ancestry --force
```

# edit ignore
```
svn propedit svn:ignore .
```
