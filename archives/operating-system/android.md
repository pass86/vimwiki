# install apk
```sh
adb install foo.apk
```

# pull app
```sh
adb pull /data/app/foo.apk
```

# pull data
```sh
adb shell
cd /data/data
cp -R foo foo_
chmod 777 -R foo_
```
```sh
adb pull /data/data/foo_
```

# log filter
```sh
adb logcat "*:W foo:V"
```

# DEX(Dalvik Executable Format)
