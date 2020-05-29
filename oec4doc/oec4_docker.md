# Environment
* Ubuntu 18.04.4 LTS
* Linux xin-Lenovo-ideapad-310-15ABR 4.15.0-99-generic #100-Ubuntu SMP Wed Apr 22 20:32:56 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
* node -v ==> v8.10.0

# Steps
```
sudo apt install npm
sudo npm install -g @angular/cli@7.3.9
sudo apt install git
sudo apt install docker.io
mkdir myapps
cd myapps
git clone https://github.com/xinxiang/oec4.git
```

# References
* https://mherman.org/blog/dockerizing-an-angular-app/

# Notes
* Angular version
```
sudo npm install -g @angular/cli
```
Installs the lastest version @angular/cli@9.1.7 
```
Node.js version v8.10.0 detected.
The Angular CLI requires a minimum Node.js version of either v10.13 or v12.0.
```
* Node version
The Dockerfile file user Node 12.2.0 as base images. 
The package.json copied from my project which is based on angular/cli@7.3.9. 
When docker build the images, many deprecated warning were given.
So I changed the @angular/cli to its latest version and the deprecated warnings were gone.

The latest Node.js is 14.3 -- https://hub.docker.com/_/node/
```
FROM node:latest
...
RUN npm install -g @angular/cli@9.1.7
```

* [docker build - Permission denied](Ref: https://stackoverflow.com/questions/48957195/how-to-fix-docker-got-permission-denied-issuexin@xin-Lenovo-ideapad-310-15ABR:~/myapps/oec4$ docker build -t oec4:dev .
)
```
> docker build -t oec4:dev .
ERRO[0000] failed to dial gRPC: cannot connect to the Docker daemon. 
Is 'docker daemon' running on this host?: 
dial unix /var/run/docker.sock: connect: permission denied 
```
Fix:
```
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
```
