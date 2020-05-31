* list containers
```
docker ps -a -q
```
* stop and remove all containers
```
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
```

# References
* https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes
* https://pythonspeed.com/articles/docker-connection-refused/
