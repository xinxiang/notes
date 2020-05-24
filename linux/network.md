# [Troubleshoot DNS](https://www.rootusers.com/how-to-troubleshoot-dns-client-issues-in-linux/)
```
/etc/nsswitch.conf
/etc/resolv.conf
/etc/hosts

# nmap -sU -p 53 192.168.0.1
...
53/udp open|filtered domain
...
# nmap -sT -p 53 192.168.0.1
...
53/tcp open  domain
...

# tcpdump -n host 192.168.0.1

# dig google.com

# whois google.com | grep -i "name server"

# dig @NS1.GOOGLE.COM google.com

```

# [Change IP](https://www.howtogeek.com/118337/stupid-geek-tricks-change-your-ip-address-from-the-command-line-in-linux/)
## Find out the interface name
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:19:84:fe:17
          inet addr:192.168.168.111  Bcast:192.168.168.255  Mask:255.255.255.0
```
## Change IP address
```
$ sudo ifconfig eth0 192.168.168.112 netmask 255.255.255.0
```
## Verify the change
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:19:84:fe:17
          inet addr:192.168.168.111  Bcast:192.168.168.255  Mask:255.255.255.0
```

## Notes:
Adjust settings in places and other servers where the IP change may affect, such as:
* /etc/host
* /etc/hosts.allow
* ufw rules 

# Change default gateway
```
$ sudo route add default gw 192.168.0.253 eth0
```

# useful commands
* Display routing table: route -n
* Verify /etc/hosts syntax: getent hosts
