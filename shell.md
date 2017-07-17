# find text
* grep -rl foo .
* ag -il --cpp foo

# find file
* find . -name foo
* ag -ig foo

# replace text
* sed -i "" "s/foo/bar/g" `grep foo -rl .`
* sed -i "" "s/foo/bar/g" `ag -il --cpp foo`
* sed -i "" "s|foo|bar|g" `ag -ilQ --cpp foo`

# current working directory
* lsof -p pid | grep cwd

# counting files
* ls -l | wc -l

# begin with
* cat foo | awk '$1 ~ /^ *\bar/'