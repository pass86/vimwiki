# install
```sh
sudo yum install samba
sudo vi /etc/samba/smb.conf
```
```
[global]
workgroup = WORKGROUP
security =  user
load printers = no
printing = bsd
printcap name = /dev/null
[share]
comment = nas share
browseable = yes
writable = yes
path = /data/share
vfs objects = full_audit recycle
full_audit:prefix = %u|%I|%m|%S
full_audit:success = mkdir rename unlink rmdir pwrite open
full_audit:failure = none
full_audit:facility = local7
full_audit:priority = NOTICE
recycle:repository = .recycle
recycle:keeptree = yes
recycle:versions = yes
```

# rsyslog on centos
```sh
sudo vi /etc/rsyslog.conf
```
```
local7.* /var/log/samba/log.audit
```
```sh
sudo systemctl restart rsyslog
```

# syslog-ng on archlinux
```sh
sudo vi /etc/syslog-ng/syslog-ng.conf
```
```sh
filter f_local7 {facility(local7);};
destination m_samba_audit { file("/var/log/samba/log.audit");  };
log { source(src); filter(f_local7);destination(m_samba_audit); flags(final);  };
```
```sh
sudo systemctl restart syslog-ng
```

# add user
```sh
sudo pdbedit -L
sudo pdbedit -a -u foo
```

# service
```sh
sudo systemctl enable smb
sudo systemctl enable nmb
sudo systemctl restart smb
sudo systemctl restart nmb
```
