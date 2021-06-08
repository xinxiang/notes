* [htop](https://www.deonsworld.co.za/2012/12/20/understanding-and-using-htop-monitor-system-resources/)
* iftop
* nethogs

```
look for open files. ... ideally before deleting. 
lsof | awk '{ print $7, $9 }' | sort -n | tail
```
