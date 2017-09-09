# pppoe
```sh
opkg update
opkg install ppp kmod-pppoe ppp-mod-pppoe
uci set network.wan.proto=pppoe
uci set network.wan.username='yougotthisfromyour@isp.su'
uci set network.wan.password='yourpassword'
uci commit network
ifup wan
```

# shadowsocks
```sh
vi /etc/opkg.conf
```
```
remove option check_signature 0
```
```sh
vi /etc/opkg/customfeeds.conf
```
```
src/gz openwrt_dist http://openwrt-dist.sourceforge.net/packages/OpenWrt/base/mvebu
src/gz openwrt_dist_luci http://openwrt-dist.sourceforge.net/packages/OpenWrt/luci
```
```sh
opkg update
opkg install shadowsocks-libev
opkg install luci-app-shadowsocks
opkg install ChinaDNS
opkg install luci-app-chinadns
reboot
```
# update chnroute
```sh
wget -O- 'http://ftp.apnic.net/apnic/stats/apnic/delegated-apnic-latest' | awk -F\| '/CN\|ipv4/ { printf("%s/%d\n", $4, 32-log($5)/log(2))  }' > /etc/chinadns_chnroute.txt
```

# guest wifi
* https://wiki.openwrt.org/doc/recipes/guest-wlan

# fix linksys wifi stability
```sh
opkg list-installed | grep mwlwifi
opkg update ; opkg install git-http ; cd /tmp ; git clone --depth 1 https://github.com/NemoAlex/mwlwifi-bin.git ; cd mwlwifi-bin/15.05.1 ; opkg install kmod-mwlwifi_3.18.23\+10.3.0.17-20160531-1_mvebu.ipk ; reboot
strings /lib/modules/*.*/mwlwifi.ko | grep "^10.3"
```

# scheduled
```sh
crontab -e
```
```
30 4 * * * sleep 70 && touch /etc/banner && reboot
40 4 * * * sleep 70 && /etc/init.d/dnsmasq restart && /etc/init.d/shadowsocks restart
```

# ddns
```sh
opkg update
opkg install ddns-scripts ddns-scripts_no-ip_com luci-app-ddns
cp /usr/lib/ddns/dynamic_dns_functions.sh /usr/lib/ddns/dynamic_dns_functions.sh.bak
vi /usr/lib/ddns/dynamic_dns_functions.sh
```
```
modify line 464
__ERR=0
```
```sh
cp /usr/lib/ddns/update_No-IP.com.sh /usr/lib/ddns/update_No-IP.com.sh.bak
vi /usr/lib/ddns/update_No-IP.com.sh
```
```
remove line 21-23
remove line 7-15
do_transfer "$__URL"
return 0
```
```sh
reboot
```

# ssh key
* local
```sh
scp ~/.ssh/id_rsa.pub root@wrt.lan:/tmp
vi ~/.ssh/config
```
```
Host wrt
    HostName wrt.lan
    User root
```
* remote
```sh
cat /tmp/id_rsa.pub >> /etc/dropbear/authorized_keys
rm /tmp/id_rsa.pub
```
