
```
root@ved ~$ docker-machine create --driver digitalocean --digitalocean-access-token=$DO_TOKEN dockerhost
Running pre-create checks...
Creating machine...
(dockerhost) Creating SSH key...
(dockerhost) Creating Digital Ocean droplet...
(dockerhost) Waiting for IP address to be assigned to the Droplet...
Waiting for machine to be running, this may take a few minutes...
Detecting operating system of created instance...
Waiting for SSH to be available...
Detecting the provisioner...
Provisioning with ubuntu(systemd)...
Installing Docker...
Copying certs to the local machine directory...
Copying certs to the remote machine...
Setting Docker configuration on the remote daemon...
Checking connection to Docker...
Docker is up and running!
To see how to connect your Docker Client to the Docker Engine running on this virtual machine, run: docker-machine env dockerhost
root@ved ~$ docker-machine env dockerhost
export DOCKER_TLS_VERIFY="1"
export DOCKER_HOST="tcp://45.55.199.154:2376"
export DOCKER_CERT_PATH="/root/.docker/machine/machines/dockerhost"
export DOCKER_MACHINE_NAME="dockerhost"
# Run this command to configure your shell:
# eval $(docker-machine env dockerhost)
root@ved ~$ docker-machine ls
NAME         ACTIVE   DRIVER         STATE     URL                         SWARM   DOCKER    ERRORS
dockerhost   -        digitalocean   Running   tcp://45.55.199.154:2376            v1.13.0
root@ved ~$ docker -H tcp://45.55.199.154:2376 ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```
```
root@ved ~$ ls /root/.docker/machine/machines/dockerhost
ca.pem  cert.pem  config.json  id_rsa  id_rsa.pub  key.pem  server-key.pem  server.pem
```
```
root@ved ~$ eval $(docker-machine env dockerhost)
```
```
root@ved ~$ docker container run -d nginx:alpine
Unable to find image 'nginx:alpine' locally
alpine: Pulling from library/nginx
b7f33cc0b48e: Pull complete
9a57e9207914: Pull complete
79f62f9c7236: Pull complete
50a2334db9bc: Pull complete
Digest: sha256:d34e2176dab830485b0cb79340e1d5ebf7d530b34ad7bfe05d269ffed20a88f4
Status: Downloaded newer image for nginx:alpine
e471c7227ddfc86c30d79323d00ebf79a20bb0fcfb335450508dba9c6e381c08
```
```
root@ved ~$ docker container ls                                                                                 
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES                                                                                              
e471c7227ddf        nginx:alpine        "nginx -g 'daemon ..."   52 seconds ago      Up 50 seconds       80/tcp, 443/tcp     hopeful_carson
```
```
root@ved ~$ docker-machine ssh dockerhost
Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-57-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  Get cloud support with Ubuntu Advantage Cloud Guest:
    http://www.ubuntu.com/business/services/cloud

75 packages can be updated.
21 updates are security updates.


*** System restart required ***
root@dockerhost:~#
```
```
root@dockerhost:~# docker container ls
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
e471c7227ddf        nginx:alpine        "nginx -g 'daemon ..."   4 minutes ago       Up 4 minutes        80/tcp, 443/tcp     hopeful_carson
root@dockerhost:~#
```
```
root@dockerhost:~# ps aux | grep dockerd
root     30130  0.4 12.3 520380 61616 ?        Ssl  10:17   0:04 /usr/bin/dockerd -H tcp://0.0.0.0:2376 -H unix:///var/run/docker.sock --storage-driver aufs --tlsverify --tlscacert /etc/docker/ca.pem --tlscert /etc/docker/server.pem --tlskey /etc/docker/server-key.pem --label provider=digitalocean
root     30620  0.0  0.1  12944   960 pts/0    S+   10:35   0:00 grep --color=auto dockerd
root@dockerhost:~#
```
```
root@dockerhost:~# exit
logout

root@ved ~$ docker-machine rm dockerhost
About to remove dockerhost
WARNING: This action will delete both local reference and remote instance.
Are you sure? (y/n): y
Successfully removed dockerhost
root@ved ~$
``` 
