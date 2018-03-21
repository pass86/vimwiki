# find text
```sh
grep -rl foo .
ag -il --cpp foo
```

# find file
```sh
find . -name foo
ag -ig foo
```

# replace text
```sh
sed -i "" "s/foo/bar/g" `grep foo -rl .`
sed -i "" "s/foo/bar/g" `ag -il --cpp foo`
sed -i "" "s|foo|bar|g" `ag -ilQ --cpp foo`
```

# current working directory
```sh
lsof -p pid | grep cwd
```

# counting files
```sh
ls -l | wc -l
```

# begin with
```sh
cat foo | awk '$1 ~ /^ *\bar/'
```

# iso to usb
```sh
dd if=foo.iso of=/dev/sdb bs=4M && sync
```

# diff two directory
```sh
diff -arq folder1 folder2
```
