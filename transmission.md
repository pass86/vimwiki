# install
* sudo yum install transmission-daemon
* sudo systemctl start transmission-daemon
* sudo systemctl stop transmission-daemon
* sudo systemctl enable transmission-daemon
* sudo vi /var/lib/transmission/.config/transmission-daemon/settings.json
    * "download-dir": "/data/share/moive"
    * "incomplete-dir": "/data/share/moive",
    * "rpc-whitelist-enabled": false,
    * "umask": 0,
* sudo systemctl start transmission-daemon