# undo last checkin
* svn merge -r HEAD:PREV path

# revert to revision
* svn merge -r HEAD:xxxx path

# up to revision
* svn up -r xxxx path

# show log
* svn log -l10 -v
* svn log -rBASE -v

# show diff
* svn log -rBASE --diff

# switch workingcopy
* svn switch http://server/proj/branches/branch1 --ignore-ancestry --force