# [iptables](https://www.howtogeek.com/177621/the-beginners-guide-to-iptables-the-linux-firewall/)
* chains: input, forward, and output.
* responses: accept, drop, reject
* states: new, established
## commands

* Policy Chain Default Behavior
```
iptables --policy [INPUT|OUTPUT|FORWARD] [ACCEPT|DROP|REJECT]
```
* Append a rule
```
iptable -A [INPUT|OUTPUT|FORWARD] -s 1.2.3.4 -j [ACCEPT|DROP|REJECT]
```
* Insert a rule
```
iptables -I [INPUT|OUTPUT|FORWARD] [NUMBER]  -s 1.2.3.4 -j [ACCEPT|DROP|REJECT]
```
* examples
```
** block all access
iptables -A INPUT -s 10.10.10.10 -j DROP

** block SSH from:
iptables -A INPUT -p tcp --dport ssh -s 10.10.10.10 -j DROP

** block SSH to:
iptables -A INPUT -p tcp --dport ssh -j DROP

** allow out block in:
iptables -A INPUT -p tcp --dport ssh -s 10.10.10.10 -m state --state NEW,ESTABLISHED -j ACCEPT

iptables -A OUTPUT -p tcp --sport 22 -d 10.10.10.10 -m state --state ESTABLISHED -j ACCEPT
```

* Save rules

** Ubuntu
```
sudo /sbin/iptables-save
```
** Red Hat / CentOS
```
/sbin/service iptables save
/etc/init.d/iptables save
```
* List rules
```
iptables -L -v
iptables -L -v | grep -i policy
```
* clear all the currently configured rules
```
iptables -F
```
