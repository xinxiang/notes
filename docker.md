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
  
# References
* https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes
* https://pythonspeed.com/articles/docker-connection-refused/
* https://hub.docker.com/_/python
* https://github.com/ixis/alpine-solr/blob/master/Dockerfile
* https://github.com/wodby/base-solr/blob/master/7.6/alpine/Dockerfile
