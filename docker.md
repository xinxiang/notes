```
docker pull ....
docker images
```
* list containers
```
docker ps -a -q
```
* stop and remove all containers
```
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
```
* remove untagged <none>:<none> images
```
docker rmi $(docker images -f "dangling=true" -q)
```
  
```
+ export 'GNUPGHOME=/tmp/gnupg_home'
+ mkdir -p /tmp/gnupg_home
+ chmod 700 /tmp/gnupg_home
+ echo disable-ipv6
+ found=
+ echo '  trying ha.pool.sks-keyservers.net for 95B01F0E78111D63D331C1A751F0CC22F625308A'
+ gpg --batch --keyserver ha.pool.sks-keyservers.net --keyserver-options 'timeout=10' --recv-keys 95B01F0E78111D63D331C1A751F0CC22F625308A
  trying ha.pool.sks-keyservers.net for 95B01F0E78111D63D331C1A751F0CC22F625308A
gpg: keybox '/tmp/gnupg_home/pubring.kbx' created
gpg: /tmp/gnupg_home/trustdb.gpg: trustdb created
gpg: key 51F0CC22F625308A: public key "Nicholas Walter Knize (CODE SIGNING KEY) <nknize@apache.org>" imported
gpg: Total number processed: 1
gpg:               imported: 1
+ found=yes
+ break
+ test -z yes
+ exit 0

```

  
# References
* https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes
* https://pythonspeed.com/articles/docker-connection-refused/
* https://hub.docker.com/_/python
* https://github.com/ixis/alpine-solr/blob/master/Dockerfile
* https://github.com/wodby/base-solr/blob/master/7.6/alpine/Dockerfile
