# install
* sudo yum install samba
* sudo vi /etc/samba/smb.conf
    * [global]
    *   workgroup = WORKGROUP
    *   security =  user
    *   load printers = no
    *   printing = bsd
    *   printcap name = /dev/null
    * [share]
    *   comment = nas share
    *   browseable = yes
    *   writable = yes
    *   path = /data/share
    *   vfs objects = full_audit recycle
    *   full_audit:prefix = %u|%I|%m|%S
    *   full_audit:success = mkdir rename unlink rmdir pwrite open
    *   full_audit:failure = none
    *   full_audit:facility = local6
    *   full_audit:priority = NOTICE
    *   recycle:repository = .recycle
    *   recycle:keeptree = yes
    *   recycle:versions = yes
* sudo vi /etc/rsyslog.conf
    * local6.* /var/log/samba/log.audit
* sudo systemctl restart rsyslog
* sudo pdbedit -L
* sudo pdbedit -a -u foo
* sudo systemctl enable smb
* sudo systemctl enable nmb
* sudo systemctl restart smb
* sudo systemctl restart nmb