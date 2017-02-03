
#What changes in Docker1.13

1) Type help command
```
root@debian:~# docker -h
Flag shorthand -h has been deprecated, please use --help                                                                  
                                                                                                                          
Usage:  docker COMMAND                                                                                                    
                                                                                                                          
A self-sufficient runtime for containers                                                                                  
                                                                                                                          
Options:                                                                                                                  
      --config string      Location of client config files (default "/root/.docker")
  -D, --debug              Enable debug mode
      --help               Print usage
  -H, --host list          Daemon socket(s) to connect to (default [])
  -l, --log-level string   Set the logging level ("debug", "info", "warn", "error", "fatal") (default "info")
      --tls                Use TLS; implied by --tlsverify
      --tlscacert string   Trust certs signed only by this CA (default "/root/.docker/ca.pem")
      --tlscert string     Path to TLS certificate file (default "/root/.docker/cert.pem")
      --tlskey string      Path to TLS key file (default "/root/.docker/key.pem")
      --tlsverify          Use TLS and verify the remote
  -v, --version            Print version information and quit

Management Commands:
  container   Manage containers
  image       Manage images
  network     Manage networks
  node        Manage Swarm nodes
  plugin      Manage plugins
  secret      Manage Docker secrets
  service     Manage services
  stack       Manage Docker stacks
  swarm       Manage Swarm
  system      Manage Docker
  volume      Manage volumes

Commands:
  attach      Attach to a running container
  build       Build an image from a Dockerfile
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes on a container's filesystem
  events      Get real time events from the server
  exec        Run a command in a running container
  export      Export a container's filesystem as a tar archive
  history     Show the history of an image
  images      List images
  import      Import the contents from a tarball to create a filesystem image
  info        Display system-wide information
  inspect     Return low-level information on Docker objects
  kill        Kill one or more running containers
  load        Load an image from a tar archive or STDIN
  login       Log in to a Docker registry
  logout      Log out from a Docker registry
  logs        Fetch the logs of a container
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  ps          List containers
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  rmi         Remove one or more images
  run         Run a command in a new container
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  search      Search the Docker Hub for images
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  version     Show the Docker version information
  wait        Block until one or more containers stop, then print their exit codes

Run 'docker COMMAND --help' for more information on a command.
```
2) Earlier we check by `docker info` to `docker system info`
```
root@debian:~# docker info
Containers: 0
 Running: 0
 Paused: 0
 Stopped: 0
Images: 0
Server Version: 1.13.0
Storage Driver: aufs
 Root Dir: /var/lib/docker/aufs
 Backing Filesystem: extfs
 Dirs: 0
 Dirperm1 Supported: true
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins: 
 Volume: local
 Network: bridge host macvlan null overlay
Swarm: inactive
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: 03e5862ec0d8d3b3f750e19fca3ee367e13c090e
runc version: 2f7393a47307a16f8cee44a37b262e8b81021e3e
init version: 949e6fa
Kernel Version: 3.16.0-4-amd64
Operating System: Debian GNU/Linux 8 (jessie)
OSType: linux
Architecture: x86_64
CPUs: 2
Total Memory: 1000 MiB
Name: debian
ID: SJFZ:FL7Y:7LJ5:XBHH:6E6I:7DPJ:XCEV:L2EY:KD5P:B7LK:KZ4U:INGE
Docker Root Dir: /var/lib/docker
Debug Mode (client): false
Debug Mode (server): false
Registry: https://index.docker.io/v1/
WARNING: No memory limit support
WARNING: No swap limit support
WARNING: No kernel memory limit support
WARNING: No oom kill disable support
WARNING: No cpu cfs quota support
WARNING: No cpu cfs period support
Experimental: false
Insecure Registries:
 127.0.0.0/8
Live Restore Enabled: false
```
```
root@debian:~# docker system info
Containers: 0
 Running: 0
 Paused: 0
 Stopped: 0
Images: 0
Server Version: 1.13.0
Storage Driver: aufs
 Root Dir: /var/lib/docker/aufs
 Backing Filesystem: extfs
 Dirs: 0
 Dirperm1 Supported: true
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins: 
 Volume: local
 Network: bridge host macvlan null overlay
Swarm: inactive
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: 03e5862ec0d8d3b3f750e19fca3ee367e13c090e
runc version: 2f7393a47307a16f8cee44a37b262e8b81021e3e
init version: 949e6fa
Kernel Version: 3.16.0-4-amd64
Operating System: Debian GNU/Linux 8 (jessie)
OSType: linux
Architecture: x86_64
CPUs: 2
Total Memory: 1000 MiB
Name: debian
ID: SJFZ:FL7Y:7LJ5:XBHH:6E6I:7DPJ:XCEV:L2EY:KD5P:B7LK:KZ4U:INGE
Docker Root Dir: /var/lib/docker
Debug Mode (client): false
Debug Mode (server): false
Registry: https://index.docker.io/v1/
WARNING: No memory limit support
WARNING: No swap limit support
WARNING: No kernel memory limit support
WARNING: No oom kill disable support
WARNING: No cpu cfs quota support
WARNING: No cpu cfs period support
Experimental: false
Insecure Registries:
 127.0.0.0/8
Live Restore Enabled: false
```
3) Container command
```
root@debian:~# docker container --help

Usage:  docker container COMMAND

Manage containers

Options:
      --help   Print usage

Commands:
  attach      Attach to a running container
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes on a container's filesystem
  exec        Run a command in a running container
  export      Export a container's filesystem as a tar archive
  inspect     Display detailed information on one or more containers
  kill        Kill one or more running containers
  logs        Fetch the logs of a container
  ls          List containers
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  prune       Remove all stopped containers
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  run         Run a command in a new container
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  wait        Block until one or more containers stop, then print their exit codes

Run 'docker container COMMAND --help' for more information on a command.
```
check running container in different views something like:
```
root@debian:~# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```
```
root@debian:~# docker container list
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

4) Image command

Type help for image
```
root@debian:~# docker image --help

Usage:  docker image COMMAND

Manage images

Options:
      --help   Print usage

Commands:
  build       Build an image from a Dockerfile
  history     Show the history of an image
  import      Import the contents from a tarball to create a filesystem image
  inspect     Display detailed information on one or more images
  load        Load an image from a tar archive or STDIN
  ls          List images
  prune       Remove unused images
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rm          Remove one or more images
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE

Run 'docker image COMMAND --help' for more information on a command.
```
```
root@debian:~# docker image list
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
```
old version we have to seen like:
```
root@debian:~# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
```
5) Use `DOCKER_HIDE_LEGACY_COMMANDS=1 docker` to hide legacy commands:
```
root@debian:~# DOCKER_HIDE_LEGACY_COMMANDS=1 docker

Usage:  docker COMMAND

A self-sufficient runtime for containers

Options:
      --config string      Location of client config files (default "/root/.docker")
  -D, --debug              Enable debug mode
      --help               Print usage
  -H, --host list          Daemon socket(s) to connect to (default [])
  -l, --log-level string   Set the logging level ("debug", "info", "warn", "error", "fatal") (default "info")
      --tls                Use TLS; implied by --tlsverify
      --tlscacert string   Trust certs signed only by this CA (default "/root/.docker/ca.pem")
      --tlscert string     Path to TLS certificate file (default "/root/.docker/cert.pem")
      --tlskey string      Path to TLS key file (default "/root/.docker/key.pem")
      --tlsverify          Use TLS and verify the remote
  -v, --version            Print version information and quit

Management Commands:
  container   Manage containers
  image       Manage images
  network     Manage networks
  node        Manage Swarm nodes
  plugin      Manage plugins
  secret      Manage Docker secrets
  service     Manage services
  stack       Manage Docker stacks
  swarm       Manage Swarm
  system      Manage Docker
  volume      Manage volumes

Commands:
  build       Build an image from a Dockerfile
  login       Log in to a Docker registry
  logout      Log out from a Docker registry
  run         Run a command in a new container
  search      Search the Docker Hub for images
  version     Show the Docker version information

Run 'docker COMMAND --help' for more information on a command.
```
6) It have advance feature in `docker system` check with help
```
root@debian:~# docker system --help

Usage:  docker system COMMAND

Manage Docker

Options:
      --help   Print usage

Commands:
  df          Show docker disk usage
  events      Get real time events from the server
  info        Display system-wide information
  prune       Remove unused data

Run 'docker system COMMAND --help' for more information on a command.
```
```
root@debian:~# docker system df
TYPE                TOTAL               ACTIVE              SIZE                RECLAIMABLE
Images              0                   0                   0 B                 0 B
Containers          0                   0                   0 B                 0 B
Local Volumes       0                   0                   0 B                 0 B
```
In old version docker we use `docker events` its change into `docker system events`
```
root@debian:~# docker system events
```
It removed unwanted when we use `docker system prune` shown like:
```
root@debian:~# docker system prune
WARNING! This will remove:
        - all stopped containers
        - all volumes not used by at least one container
        - all networks not used by at least one container
        - all dangling images
Are you sure you want to continue? [y/N] y
Total reclaimed space: 0 B
```
7) In `docker build` option `-q` argument added when we use `-q` an it remove intermediate containers
    after a successful build or many more etc. Press --help.
```
root@debian:~# docker build --help

Usage:  docker build [OPTIONS] PATH | URL | -

Build an image from a Dockerfile

Options:
      --build-arg list             Set build-time variables (default [])
      --cache-from stringSlice     Images to consider as cache sources
      --cgroup-parent string       Optional parent cgroup for the container
      --compress                   Compress the build context using gzip
      --cpu-period int             Limit the CPU CFS (Completely Fair Scheduler) period
      --cpu-quota int              Limit the CPU CFS (Completely Fair Scheduler) quota
  -c, --cpu-shares int             CPU shares (relative weight)
      --cpuset-cpus string         CPUs in which to allow execution (0-3, 0,1)
      --cpuset-mems string         MEMs in which to allow execution (0-3, 0,1)
      --disable-content-trust      Skip image verification (default true)
  -f, --file string                Name of the Dockerfile (Default is 'PATH/Dockerfile')
      --force-rm                   Always remove intermediate containers
      --help                       Print usage
      --isolation string           Container isolation technology
      --label list                 Set metadata for an image (default [])
  -m, --memory string              Memory limit
      --memory-swap string         Swap limit equal to memory plus swap: '-1' to enable unlimited swap
      --network string             Set the networking mode for the RUN instructions during build (default "default")
      --no-cache                   Do not use cache when building the image
      --pull                       Always attempt to pull a newer version of the image
  -q, --quiet                      Suppress the build output and print image ID on success
      --rm                         Remove intermediate containers after a successful build (default true)
      --security-opt stringSlice   Security options
      --shm-size string            Size of /dev/shm, default value is 64MB
  -t, --tag list                   Name and optionally a tag in the 'name:tag' format (default [])
      --ulimit ulimit              Ulimit options (default [])
```
8) Docker swarm 
ver 1.13
```
root@debian:~# docker swarm --help

Usage:  docker swarm COMMAND

Manage Swarm

Options:
      --help   Print usage

Commands:
  init        Initialize a swarm
  join        Join a swarm as a node and/or manager
  join-token  Manage join tokens
  leave       Leave the swarm
  unlock      Unlock swarm
  unlock-key  Manage the unlock key
  update      Update the swarm

Run 'docker swarm COMMAND --help' for more information on a command.
```
ver 1.12
```
[root@fedora ~]# docker swarm --help

Usage:  docker swarm COMMAND

Manage Docker Swarm

Options:
      --help   Print usage

Commands:
  init        Initialize a swarm
  join        Join a swarm as a node and/or manager
  join-token  Manage join tokens
  update      Update the swarm
  leave       Leave the swarm (workers only)

Run 'docker swarm COMMAND --help' for more information on a command.
```
9) Docker Plugin new in ver 1.13
```
root@debian:~# docker plugin --help

Usage:  docker plugin COMMAND

Manage plugins

Options:
      --help   Print usage

Commands:
  create      Create a plugin from a rootfs and configuration. Plugin data directory must contain config.json and rootfs directory.
  disable     Disable a plugin
  enable      Enable a plugin
  inspect     Display detailed information on one or more plugins
  install     Install a plugin
  ls          List plugins
  push        Push a plugin to a registry
  rm          Remove one or more plugins
  set         Change settings for a plugin

Run 'docker plugin COMMAND --help' for more information on a command.
```
10) In `docker service` command
```
root@debian:~# docker service --help
                                                                                                                                                     
Usage:  docker service COMMAND                                                                                                                       
                                                                                                                                                     
Manage services

Options:
      --help   Print usage

Commands:
  create      Create a new service
  inspect     Display detailed information on one or more services
  ls          List services
  ps          List the tasks of a service
  rm          Remove one or more services
  scale       Scale one or multiple replicated services
  update      Update a service

Run 'docker service COMMAND --help' for more information on a command.
```
```
root@debian:~# docker service update --help

Usage:  docker service update [OPTIONS] SERVICE

Update a service

Options:
      --args string                      Service command args
      --constraint-add list              Add or update a placement constraint (default [])
      --constraint-rm list               Remove a constraint (default [])
      --container-label-add list         Add or update a container label (default [])
      --container-label-rm list          Remove a container label by its key (default [])
      --dns-add list                     Add or update a custom DNS server (default [])
      --dns-option-add list              Add or update a DNS option (default [])
      --dns-option-rm list               Remove a DNS option (default [])
      --dns-rm list                      Remove a custom DNS server (default [])
      --dns-search-add list              Add or update a custom DNS search domain (default [])
      --dns-search-rm list               Remove a DNS search domain (default [])
      --endpoint-mode string             Endpoint mode (vip or dnsrr)
      --env-add list                     Add or update an environment variable (default [])
      --env-rm list                      Remove an environment variable (default [])
      --force                            Force update even if no changes require it
      --group-add list                   Add an additional supplementary user group to the container (default [])
      --group-rm list                    Remove a previously added supplementary user group from the container (default [])
      --health-cmd string                Command to run to check health
      --health-interval duration         Time between running the check (ns|us|ms|s|m|h) (default none)
      --health-retries int               Consecutive failures needed to report unhealthy
      --health-timeout duration          Maximum time to allow one check to run (ns|us|ms|s|m|h) (default none)
      --help                             Print usage
      --host-add list                    Add or update a custom host-to-IP mapping (host:ip) (default [])
      --host-rm list                     Remove a custom host-to-IP mapping (host:ip) (default [])
      --hostname string                  Container hostname
      --image string                     Service image tag
      --label-add list                   Add or update a service label (default [])
      --label-rm list                    Remove a label by its key (default [])
      --limit-cpu decimal                Limit CPUs (default 0.000)
      --limit-memory bytes               Limit Memory (default 0 B)
      --log-driver string                Logging driver for service
      --log-opt list                     Logging driver options (default [])
      --mount-add mount                  Add or update a mount on a service
      --mount-rm list                    Remove a mount by its target path (default [])
      --no-healthcheck                   Disable any container-specified HEALTHCHECK
      --publish-add port                 Add or update a published port
      --publish-rm port                  Remove a published port by its target port
      --replicas uint                    Number of tasks (default none)
      --reserve-cpu decimal              Reserve CPUs (default 0.000)
      --reserve-memory bytes             Reserve Memory (default 0 B)
      --restart-condition string         Restart when condition is met (none, on-failure, or any)
      --restart-delay duration           Delay between restart attempts (ns|us|ms|s|m|h) (default none)
      --restart-max-attempts uint        Maximum number of restarts before giving up (default none)
      --restart-window duration          Window used to evaluate the restart policy (ns|us|ms|s|m|h) (default none)
      --rollback                         Rollback to previous specification
      --secret-add secret                Add or update a secret on a service
      --secret-rm list                   Remove a secret (default [])
      --stop-grace-period duration       Time to wait before force killing a container (ns|us|ms|s|m|h) (default none)
  -t, --tty                              Allocate a pseudo-TTY
      --update-delay duration            Delay between updates (ns|us|ms|s|m|h) (default 0s)
      --update-failure-action string     Action on update failure (pause|continue) (default "pause")
      --update-max-failure-ratio float   Failure rate to tolerate during an update
      --update-monitor duration          Duration after each task update to monitor for failure (ns|us|ms|s|m|h) (default 0s)
      --update-parallelism uint          Maximum number of tasks updated simultaneously (0 to update all at once) (default 1)
  -u, --user string                      Username or UID (format: <name|uid>[:<group|gid>])
      --with-registry-auth               Send registry authentication details to swarm agents
  -w, --workdir string                   Working directory inside the container
  ```
 ##Example of `docker plugin` how we use it.
  
  ###Lab 

There are three virtual machine like `vm1`, `vm2`, and `vm3`

Acoording to Docker meetup video we have to start from vm2

In vm2 

started with `docker plugin` --help command
```
root@vm2:~# docker plugin --help

Usage:  docker plugin COMMAND

Manage plugins

Options:
      --help   Print usage

Commands:
  create      Create a plugin from a rootfs and configuration. Plugin data directory must contain config.json and rootfs directory.
  disable     Disable a plugin
  enable      Enable a plugin
  inspect     Display detailed information on one or more plugins
  install     Install a plugin
  ls          List plugins
  push        Push a plugin to a registry
  rm          Remove one or more plugins
  set         Change settings for a plugin

Run 'docker plugin COMMAND --help' for more information on a command.
root@vm2:~#
```

This is the process how we install `docker plugin` which make enable, disable or inspect. 
```
root@vm2:~# docker plugin install vieux/sshfs
Plugin "vieux/sshfs" is requesting the following privileges:
 - network: [host]
 - device: [/dev/fuse]
 - capabilities: [CAP_SYS_ADMIN]
Do you grant the above permissions? [y/N] y
latest: Pulling from vieux/sshfs
ca06593c3b54: Download complete
Digest: sha256:660b5302a6951aa1c47c3042ca288d16973f236adbd2f77fc5571f164143adf5
Status: Downloaded newer image for vieux/sshfs:latest
Installed plugin vieux/sshfs
root@vm2:~#
```
```
root@vm2:~# docker plugin list
ID                  NAME                 DESCRIPTION               ENABLED
404d489a9b96        vieux/sshfs:latest   sshFS plugin for Docker   true
root@vm2:~#
```
when we install docker plugin without add argument env `DEBUG` it will be `0`. we can also use it to install like `docker plugin install vieux/sshfs:latest DEBUG=1 `

we give trick how we add or make it in another example below we can make it `DEBUG=1`:

```
root@vm2:~# docker plugin inspect vieux/sshfs:latest
[
    {
        "Config": {
            "Args": {
                "Description": "",
                "Name": "",
                "Settable": null,
                "Value": null
            },
            "Description": "sshFS plugin for Docker",
            "Documentation": "https://docs.docker.com/engine/extend/plugins/",
            "Entrypoint": [
                "/docker-volume-sshfs"
            ],
            "Env": [
                {
                    "Description": "",
                    "Name": "DEBUG",
                    "Settable": [
                        "value"
                    ],
                    "Value": "0"
                }
            ],
            "Interface": {
                "Socket": "sshfs.sock",
                "Types": [
                    "docker.volumedriver/1.0"
                ]
            },
            "Linux": {
                "AllowAllDevices": false,
                "Capabilities": [
                    "CAP_SYS_ADMIN"
                ],
                "Devices": [
                    {
                        "Description": "",
                        "Name": "",
                        "Path": "/dev/fuse",
                        "Settable": null
                    }
                ]
            },
            "Mounts": null,
            "Network": {
                "Type": "host"
            },
            "PropagatedMount": "/mnt",
            "User": {},
            "WorkDir": "",
            "rootfs": {
                "diff_ids": [
                    "sha256:0f70aa9391794138ca1b4db149027f1c56ce28136b0eba522bd8af7ea09bfb84"
                ],
                "type": "layers"
            }
        },
        "Enabled": true,
        "Id": "404d489a9b964279b4216adfddd51af1aec4607b14a0e44964d784f1eaa05963",
        "Name": "vieux/sshfs:latest",
        "Settings": {
            "Args": [],
            "Devices": [
                {
                    "Description": "",
                    "Name": "",
                    "Path": "/dev/fuse",
                    "Settable": null
                }
            ],
            "Env": [
                "DEBUG=0"
            ],
            "Mounts": []
        }
    }
]
root@vm2:~#
```
First disable running plugin or how we disable the plugin.
```
root@vm2:~# docker plugin disable  vieux/sshfs:latest
vieux/sshfs:latest
```
Need to set the previous plugin `vieux/sshfs`. and make debug mode.

check by help `docker plugin set`
```
root@vm2:~# docker plugin set --help

Usage:  docker plugin set PLUGIN KEY=VALUE [KEY=VALUE...]

Change settings for a plugin

Options:
      --help   Print usage
```
Use `DEBUG=1` option need to set.
```
root@vm2:~# docker plugin set vieux/sshfs DEBUG=1
```
check list of plugin by `docker plugin list`. Its is false.
```
root@vm2:~# docker plugin list
ID                  NAME                 DESCRIPTION               ENABLED
404d489a9b96        vieux/sshfs:latest   sshFS plugin for Docker   false
root@vm2:~# docker plugin enable vieux/sshfs:latest
vieux/sshfs:latest
```
Now enable the plugin
```
root@vm2:~# docker plugin enable vieux/sshfs:latest
vieux/sshfs:latest
```
```
root@vm2:~# docker plugin list
ID                  NAME                 DESCRIPTION               ENABLED
404d489a9b96        vieux/sshfs:latest   sshFS plugin for Docker   true
```
check list of plugin by `docker plugin list`. Its is true.
```
root@vm2:~# docker plugin inspect vieux/sshfs:latest
[
    {
        "Config": {
            "Args": {
                "Description": "",
                "Name": "",
                "Settable": null,
                "Value": null
            },
            "Description": "sshFS plugin for Docker",
            "Documentation": "https://docs.docker.com/engine/extend/plugins/",
            "Entrypoint": [
                "/docker-volume-sshfs"
            ],
            "Env": [
                {
                    "Description": "",
                    "Name": "DEBUG",
                    "Settable": [
                        "value"
                    ],
                    "Value": "0"
                }
            ],
            "Interface": {
                "Socket": "sshfs.sock",
                "Types": [
                    "docker.volumedriver/1.0"
                ]
            },
            "Linux": {
                "AllowAllDevices": false,
                "Capabilities": [
                    "CAP_SYS_ADMIN"
                ],
                "Devices": [
                    {
                        "Description": "",
                        "Name": "",
                        "Path": "/dev/fuse",
                        "Settable": null
                    }
                ]
            },
            "Mounts": null,
            "Network": {
                "Type": "host"
            },
            "PropagatedMount": "/mnt",
            "User": {},
            "WorkDir": "",
            "rootfs": {
                "diff_ids": [
                    "sha256:0f70aa9391794138ca1b4db149027f1c56ce28136b0eba522bd8af7ea09bfb84"
                ],
                "type": "layers"
            }
        },
        "Enabled": true,
        "Id": "404d489a9b964279b4216adfddd51af1aec4607b14a0e44964d784f1eaa05963",
        "Name": "vieux/sshfs:latest",
        "Settings": {
            "Args": [],
            "Devices": [
                {
                    "Description": "",
                    "Name": "",
                    "Path": "/dev/fuse",
                    "Settable": null
                }
            ],
            "Env": [
                "DEBUG=1"
            ],
            "Mounts": []
        }
    }
]
root@vm2:~#
```
In vm3
First install plugin `vieux/sshfs` in `DEBUG=1`
```
root@vm3:~# docker plugin install vieux/sshfs DEBUG=1
Plugin "vieux/sshfs" is requesting the following privileges:
 - network: [host]
 - device: [/dev/fuse]
 - capabilities: [CAP_SYS_ADMIN]
Do you grant the above permissions? [y/N] y
latest: Pulling from vieux/sshfs
ca06593c3b54: Download complete
Digest: sha256:660b5302a6951aa1c47c3042ca288d16973f236adbd2f77fc5571f164143adf5
Status: Downloaded newer image for vieux/sshfs:latest
Installed plugin vieux/sshfs
root@vm3:~#
```
If don't understand  step we use `--help`.
```
root@vm3:~# docker plugin install --help

Usage:  docker plugin install [OPTIONS] PLUGIN [KEY=VALUE...]

Install a plugin

Options:
      --alias string            Local name for plugin
      --disable                 Do not enable the plugin on install
      --disable-content-trust   Skip image verification (default true)
      --grant-all-permissions   Grant all permissions necessary to run the plugin
      --help                    Print usage
```
First we create directory in `vm1` name is `shared` in tmp directory. or may we can create file name is `world`.
```
[root@vm1 tmp]# mkdir shared
[root@vm1 tmp]# ls
shared  vboxguest-Module.symvers
[root@vm1 tmp]# cd shared/
[root@vm1 shared]# ls
[root@vm1 shared]# echo hello > world
[root@vm1 shared]# ls
world
```

Earlier we have an add plugin `vieux/sshfs` we can use to create an volume in `vm1` in `/tmp/shared/` directory and volume name will be `sshvolume`.
```
[root@vm3 ~]# docker volume create -d vieux/sshfs -o sshcmd=root@192.168.56.201:/tmp/shared -o password=redhat sshvolume
sshvolume
[root@vm3 ~]# docker volume list
DRIVER               VOLUME NAME
vieux/sshfs:latest   sshvolume
```
Mount the `sshvolume` volume in `alpine` image in `/data`.
```
[root@vm3 code]# docker run -it -v sshvolume:/data  alpine sh
Unable to find image 'alpine:latest' locally
latest: Pulling from library/alpine
0a8490d0dfd3: Pull complete 
Digest: sha256:dfbd4a3a8ebca874ebd2474f044a0b33600d4523d03b0df76e5c5986cb02d7e8
Status: Downloaded newer image for alpine:latest
/ # cd /data/
/data # ls
world
/data # touch {1..9}
/data # ls
world   {1..9}
```

We can also use this step in `vm2`.
```
[root@vm2 ~]# docker volume create -d vieux/sshfs -o sshcmd=root@192.168.56.201:/tmp/shared -o password=redhat sshvolume
sshvolume
```
```
[root@vm2 ~]# docker volume list
DRIVER               VOLUME NAME
vieux/sshfs:latest   sshvolume
```
Finally its works
```
[root@vm2 code]# docker run -it -v sshvolume:/data  alpine sh
Unable to find image 'alpine:latest' locally
latest: Pulling from library/alpine
0a8490d0dfd3: Pull complete 
Digest: sha256:dfbd4a3a8ebca874ebd2474f044a0b33600d4523d03b0df76e5c5986cb02d7e8
Status: Downloaded newer image for alpine:latest
/ # cd /data/
/data # ls
/data # ls
world   {1..9}
```

We can also use this above step in `docker swarm`.

Initialize a swarm in `vm1`.

```
[root@vm1 ~]# docker swarm init --advertise-addr 192.168.56.201
Swarm initialized: current node (e4fp9b0ud7fjldf58abnm6bzf) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join \
    --token SWMTKN-1-5pg4jmfnvnva8c54qa6uhfhjuweu80js1mhd7egh76cayy3qrh-9ppwh7c29brlciaaxkxcehlij \
    192.168.56.201:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
```
`vm2` `vm3` join a swarm as a node.
```
[root@vm2 ~]# docker swarm join \
>     --token SWMTKN-1-5pg4jmfnvnva8c54qa6uhfhjuweu80js1mhd7egh76cayy3qrh-9ppwh7c29brlciaaxkxcehlij \
>     192.168.56.201:2377
This node joined a swarm as a worker.
```
```
[root@vm3 ~]# docker swarm join \
>     --token SWMTKN-1-5pg4jmfnvnva8c54qa6uhfhjuweu80js1mhd7egh76cayy3qrh-9ppwh7c29brlciaaxkxcehlij \
>     192.168.56.201:2377
This node joined a swarm as a worker.
```

Check list of node by `docker node list`.
```
[root@vm1 ~]# docker node list
ID                           HOSTNAME  STATUS  AVAILABILITY  MANAGER STATUS
3ijcv6et88g81sq9thjhlfl7t    vm2       Ready   Active
e4fp9b0ud7fjldf58abnm6bzf *  vm1       Ready   Active        Leader
nxu8s5frib7ntn8fuc4babepq    vm3       Ready   Active
```
Check list of running container by `docker container list` we also use as old like `docker ps`.
```
[root@vm1 ~]# docker container list
CONTAINER ID        IMAGE          COMMAND           CREATED           STATUS            PORTS             NAMES
```
First we need to help how to use docker service check by `docker service help`.
```
root@vm1:~# docker service --help

Usage:  docker service COMMAND

Manage services

Options:
      --help   Print usage

Commands:
  create      Create a new service
  inspect     Display detailed information on one or more services
  ls          List services
  ps          List the tasks of a service
  rm          Remove one or more services
  scale       Scale one or multiple replicated services
  update      Update a service

Run 'docker service COMMAND --help' for more information on a command.
```
We can also use `docker service create --help` beacause many option added from previous version.
```
root@vm1:~# docker service create --help
                                                                                                                                      
Usage:  docker service create [OPTIONS] IMAGE [COMMAND] [ARG...]                                                                      
                                                                                                                                                     
Create a new service                                                                                                                                                    
                                                                                                                                                                        
Options:                                                                                                                                                                
      --constraint list                  Placement constraints (default [])                                                                                             
      --container-label list             Container labels (default [])
      --dns list                         Set custom DNS servers (default [])
      --dns-option list                  Set DNS options (default [])
      --dns-search list                  Set custom DNS search domains (default [])
      --endpoint-mode string             Endpoint mode (vip or dnsrr)
  -e, --env list                         Set environment variables (default [])
      --env-file list                    Read in a file of environment variables (default [])
      --group list                       Set one or more supplementary user groups for the container (default [])
      --health-cmd string                Command to run to check health
      --health-interval duration         Time between running the check (ns|us|ms|s|m|h) (default none)
      --health-retries int               Consecutive failures needed to report unhealthy
      --health-timeout duration          Maximum time to allow one check to run (ns|us|ms|s|m|h) (default none)
      --help                             Print usage
      --host list                        Set one or more custom host-to-IP mappings (host:ip) (default [])
      --hostname string                  Container hostname
  -l, --label list                       Service labels (default [])
      --limit-cpu decimal                Limit CPUs (default 0.000)
      --limit-memory bytes               Limit Memory (default 0 B)
      --log-driver string                Logging driver for service
      --log-opt list                     Logging driver options (default [])
      --mode string                      Service mode (replicated or global) (default "replicated")
      --mount mount                      Attach a filesystem mount to the service
      --name string                      Service name
      --network list                     Network attachments (default [])
      --no-healthcheck                   Disable any container-specified HEALTHCHECK
  -p, --publish port                     Publish a port as a node port
      --replicas uint                    Number of tasks (default none)
      --reserve-cpu decimal              Reserve CPUs (default 0.000)
      --reserve-memory bytes             Reserve Memory (default 0 B)
      --restart-condition string         Restart when condition is met (none, on-failure, or any)
      --restart-delay duration           Delay between restart attempts (ns|us|ms|s|m|h) (default none)
      --restart-max-attempts uint        Maximum number of restarts before giving up (default none)
      --restart-window duration          Window used to evaluate the restart policy (ns|us|ms|s|m|h) (default none)
      --secret secret                    Specify secrets to expose to the service
      --stop-grace-period duration       Time to wait before force killing a container (ns|us|ms|s|m|h) (default none)
  -t, --tty                              Allocate a pseudo-TTY
      --update-delay duration            Delay between updates (ns|us|ms|s|m|h) (default 0s)
      --update-failure-action string     Action on update failure (pause|continue) (default "pause")
      --update-max-failure-ratio float   Failure rate to tolerate during an update
      --update-monitor duration          Duration after each task update to monitor for failure (ns|us|ms|s|m|h) (default 0s)
      --update-parallelism uint          Maximum number of tasks updated simultaneously (0 to update all at once) (default 1)
  -u, --user string                      Username or UID (format: <name|uid>[:<group|gid>])
      --with-registry-auth               Send registry authentication details to swarm agents
  -w, --workdir string                   Working directory inside the container
```
Create new service mount volume `sshvolume` that can attach a filesystem mount to the service and destination directory will be `/data` in alpine image with 2 replicas.
```
[root@vm1 ~]# docker service create --mount src=sshvolume,dst=/data --replicas 2 --name foo alpine sh -c "while true;do echo \`cat /etc/hostname\` >> /data/hostnames; sleep 1; done"
arh5p9k6pitokwau78ul33y28
```
Check services list by `docker service list`
```
[root@vm1 ~]# docker service list
ID            NAME  MODE        REPLICAS  IMAGE
arh5p9k6pito  foo   replicated  2/2       alpine:latest
[root@vm1 ~]#
```
Also check list of container by `docker container list`
```
[root@vm1 ~]# docker container list
CONTAINER ID        IMAGE                                                                            COMMAND                  CREATED             STATUS              PORTS               NAMES
23320a295c9a        alpine@sha256:dfbd4a3a8ebca874ebd2474f044a0b33600d4523d03b0df76e5c5986cb02d7e8   "sh -c 'while true..."   7 minutes ago       Up 7 minutes                            foo.2.rcqsxhhabpmnmrwszqu98wm73
```
List the tasks of a service by `docker service ps foo`
```
[root@vm1 ~]# docker service ps foo
ID            NAME   IMAGE          NODE  DESIRED STATE  CURRENT STATE          ERROR  PORTS
i7a7ljvjapf2  foo.1  alpine:latest  vm2   Running        Running 3 minutes ago
rcqsxhhabpmn  foo.2  alpine:latest  vm1   Running        Running 2 minutes ago
[root@vm1 ~]#
```
Finally, go to vm1 use below step.
```
[root@vm1 ~]# cd /tmp/shared/
[root@vm1 shared]# ls
{1..9}  hostnames  world
```
```
[root@vm1 shared]# cat hostnames 
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
[root@vm1 shared]#
```
```
[root@vm1 shared]# cat hostnames | less

cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
cbd14efe1392
:
```
#COMPOSE TO SWARM 
Stack is new in Docker 1.13. So, how can we use following step:

An it will an applicable when `docker swarm` initialized

Check help by `docker stack --help` and what type of option or argment use.
```
[root@vm1 ~]# docker stack --help

Usage:  docker stack COMMAND

Manage Docker stacks

Options:
      --help   Print usage

Commands:
  deploy      Deploy a new stack or update an existing stack
  ls          List stacks
  ps          List the tasks in the stack
  rm          Remove the stack
  services    List the services in the stack

Run 'docker stack COMMAND --help' for more information on a command.
[root@vm1 ~]#
```
Check help for deploy or up by `docker stack deploy --help`.
```
[root@vm1 ~]# docker stack deploy --help

Usage:  docker stack deploy [OPTIONS] STACK

Deploy a new stack or update an existing stack

Aliases:
  deploy, up

Options:
  -c, --compose-file string   Path to a Compose file
      --help                  Print usage
      --with-registry-auth    Send registry authentication details to Swarm agents
[root@vm1 ~]#
```
Take old version compose file and change in to version 2 to 3 in `docker-compose.yml`.

we have to take https://github.com/cloudyuga/rsvpapp.git

Clone a repository from github
```
[root@vm1 ~]# git clone https://github.com/cloudyuga/rsvpapp.git
Cloning into 'rsvpapp'...
remote: Counting objects: 247, done.
remote: Compressing objects: 100% (24/24), done.
remote: Total 247 (delta 9), reused 0 (delta 0), pack-reused 222
Receiving objects: 100% (247/247), 102.27 KiB | 0 bytes/s, done.
Resolving deltas: 100% (115/115), done.
Checking connectivity... done.
```
change the directory or go to `rsvpapp`
```
[root@vm1 ~]# cd rsvpapp/
```
If we deploy from older version they can't be supported.
```
[root@vm1 rsvpapp]# docker stack deploy -c docker-compose.yml FOO
Unsupported Compose file version: "2". The only version supported is "3" (or "3.0")
```
we can change version 2 into 3

berfore
```
[root@vm1 rsvpapp]# nano docker-compose.yml
version: '2'
services:
 mongodb:
   image: mongo:3.3   
   expose:                 
     - "27017"
   volumes:
     - db_data:/data/db
   environment:    
    MONGODB_DATABASE: rsvpdata
   networks:
    - rsvpnet

 web:
   image: teamcloudyuga/rsvpapp:mooc
   ports:
    - "5000:5000"
   environment:
    MONGODB_HOST: mongodb
    LINK: http://www.meetup.com/cloudyuga/
    TEXT1: CloudYuga 
    TEXT2: Garage RSVP!
    LOGO: https://raw.githubusercontent.com/cloudyuga/rsvpapp/master/static/cloudyuga.png
    COMPANY: CloudYuga Technology Pvt. Ltd.
   networks:
    - rsvpnet

networks:
  rsvpnet:

volumes:
   db_data:
```
After
```
[root@vm1 rsvpapp]# nano docker-compose.yml
version: '3'
services:
 mongodb:
   image: mongo:3.3   
   expose:                 
     - "27017"
   volumes:
     - db_data:/data/db
   environment:    
    MONGODB_DATABASE: rsvpdata
   networks:
    - rsvpnet

 web:
   image: teamcloudyuga/rsvpapp:mooc
   ports:
    - "5000:5000"
   environment:
    MONGODB_HOST: mongodb
    LINK: http://www.meetup.com/cloudyuga/
    TEXT1: CloudYuga 
    TEXT2: Garage RSVP!
    LOGO: https://raw.githubusercontent.com/cloudyuga/rsvpapp/master/static/cloudyuga.png
    COMPANY: CloudYuga Technology Pvt. Ltd.
   networks:
    - rsvpnet

networks:
  rsvpnet:

volumes:
   db_data:
```
```
```
[root@vm1 rsvpapp]# docker stack deploy -c docker-compose.yml FOO
Ignoring deprecated options:

expose: Exposing ports is unnecessary - services on the same network can access each other's containers on any port.

Creating network FOO_rsvpnet
Creating service FOO_mongodb
Creating service FOO_web
[root@vm1 rsvpapp]# docker stack list
NAME  SERVICES
FOO   2
[root@vm1 rsvpapp]#
```
```
[root@vm1 rsvpapp]# docker stack services FOO
ID            NAME         MODE        REPLICAS  IMAGE
fwbn4uvu3jos  FOO_web      replicated  1/1       teamcloudyuga/rsvpapp:mooc
w5fm9e07hgl0  FOO_mongodb  replicated  1/1       mongo:3.3
[root@vm1 rsvpapp]#
```
```
[root@vm1 rsvpapp]# docker stack rm FOO
Removing service FOO_web
Removing service FOO_mongodb
Removing network FOO_rsvpnet
```
##Reference
https://docs.docker.com/docker-cloud/getting-started/deploy-app/11_service_stacks/
