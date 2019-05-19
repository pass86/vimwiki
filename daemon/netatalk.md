# Install
Download snapshot
https://aur.archlinux.org/packages/netatalk/
```sh
makepkg -si
```

# Configuration
```sh
sudo mkdir /data/timemachine
sudo chown foo:foo /data/timemachine
sudo vim /etc/afp.conf
```
```ini
[Global]
log level = default:info
log file = /var/log/afpd.log

[TimeMachine]
path = /data/timemachine
vol size limit = 1000000
time machine = yes
valid users = foo
```
```sh
sudo systemctl enable netatalk
sudo systemctl start netatalk
sudo systemctl enable avahi-daemon
sudo systemctl start avahi-daemon
```
