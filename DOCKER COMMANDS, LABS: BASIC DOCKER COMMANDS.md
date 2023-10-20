### What is the version of Docker Server Engine running on the Host?
```ruby
$ docker version

Client: Docker Engine - Community
 Version:           20.10.24
 API version:       1.41
 Go version:        go1.19.7
 Git commit:        297e128
 Built:             Tue Apr  4 18:21:05 2023
 OS/Arch:           linux/amd64
 Context:           default
 Experimental:      true

Server: Docker Engine - Community
 Engine:
  Version:          20.10.24
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.19.7
  Git commit:       5d6db84
  Built:            Tue Apr  4 18:18:48 2023
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.6.20
  GitCommit:        2806fc1057397dbaeefbea0e4e17bddfbd388f38
 runc:
  Version:          1.1.5
  GitCommit:        v1.1.5-0-gf19387a
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
```

### How many images are available on this host?

```ruby
$ docker images

REPOSITORY                      TAG       IMAGE ID       CREATED        SIZE
redis                           latest    eca1379fe8b5   6 months ago   117MB
mysql                           latest    8189e588b0e8   6 months ago   564MB
nginx                           latest    6efc10a0510f   6 months ago   142MB
postgres                        latest    ceccf204404e   6 months ago   379MB
nginx                           alpine    8e75cbc5b25c   6 months ago   41MB
alpine                          latest    9ed4aefc74f6   6 months ago   7.04MB
ubuntu                          latest    08d22c0ceb15   7 months ago   77.8MB
kodekloud/simple-webapp-mysql   latest    129dd9f67367   5 years ago    96.6MB
kodekloud/simple-webapp         latest    c6e3cd9aae36   5 years ago    84.8MB
```

### Run a container using the redis image

```ruby
$ docker run redis

1:C 20 Oct 2023 04:37:50.953 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
1:C 20 Oct 2023 04:37:50.954 # Redis version=7.0.11, bits=64, commit=00000000, modified=0, pid=1, just started
1:C 20 Oct 2023 04:37:50.954 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
1:M 20 Oct 2023 04:37:50.954 * monotonic clock: POSIX clock_gettime
1:M 20 Oct 2023 04:37:50.955 * Running mode=standalone, port=6379.
1:M 20 Oct 2023 04:37:50.955 # Server initialized
1:M 20 Oct 2023 04:37:50.956 # WARNING Memory overcommit must be enabled! Without it, a background save or replication may fail under low memory condition. Being disabled, it can can also cause failures without low memory condition, see https://github.com/jemalloc/jemalloc/issues/1328. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
1:M 20 Oct 2023 04:37:50.956 * Ready to accept connections

```

### Stop the container you just createdHit CTRL+C if you are on the container's terminal. Or else run docker stop <container-id>.

hint:Hit CTRL+C if you are on the container's terminal. Or else run docker stop <container-id>.

```ruby
^C1:signal-handler (1697776789) Received SIGINT scheduling shutdown...
1:M 20 Oct 2023 04:39:49.213 # User requested shutdown...
1:M 20 Oct 2023 04:39:49.213 * Saving the final RDB snapshot before exiting.
1:M 20 Oct 2023 04:39:49.217 * DB saved on disk
1:M 20 Oct 2023 04:39:49.217 # Redis is now ready to exit, bye bye...
$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
$ docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS                      PORTS     NAMES
868707999e0a   redis     "docker-entrypoint.s…"   2 minutes ago   Exited (0) 10 seconds ago             stoic_khayyam
$ 
```

###  How many containers are RUNNING on this host now?

```ruby
$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

```

### How many containers are PRESENT on the host now?


Including both Running and Not Running ones
```ruby
$ docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS                          PORTS     NAMES
a31be71c418a   alpine         "/bin/sh"                About a minute ago   Exited (0) About a minute ago             thirsty_northcutt
685e98a9dbd8   alpine         "sleep 1000"             About a minute ago   Up About a minute                         vibrant_swirles
10ea03111e51   nginx:alpine   "/docker-entrypoint.…"   About a minute ago   Up About a minute               80/tcp    nginx-2
a70c20dfc8d2   nginx:alpine   "/docker-entrypoint.…"   About a minute ago   Up About a minute               80/tcp    nginx-1
a89b947b7ddf   ubuntu         "sleep 1000"             About a minute ago   Up About a minute                         awesome_northcut
868707999e0a   redis          "docker-entrypoint.s…"   7 minutes ago        Exited (0) 5 minutes ago                  stoic_khayyam
```

### What is the image used to run the nginx-1 container?
```ruby
$ docker ps 
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS     NAMES
685e98a9dbd8   alpine         "sleep 1000"             3 minutes ago   Up 3 minutes             vibrant_swirles
10ea03111e51   nginx:alpine   "/docker-entrypoint.…"   3 minutes ago   Up 3 minutes   80/tcp    nginx-2
a70c20dfc8d2   nginx:alpine   "/docker-entrypoint.…"   3 minutes ago   Up 3 minutes   80/tcp    nginx-1
a89b947b7ddf   ubuntu         "sleep 1000"             3 minutes ago   Up 3 minutes             awesome_northcut
$ 
```
### What is the name of the container created using the ubuntu image?
```ruby
$ docker ps 
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS     NAMES
685e98a9dbd8   alpine         "sleep 1000"             3 minutes ago   Up 3 minutes             vibrant_swirles
10ea03111e51   nginx:alpine   "/docker-entrypoint.…"   3 minutes ago   Up 3 minutes   80/tcp    nginx-2
a70c20dfc8d2   nginx:alpine   "/docker-entrypoint.…"   3 minutes ago   Up 3 minutes   80/tcp    nginx-1
a89b947b7ddf   ubuntu         "sleep 1000"             3 minutes ago   Up 3 minutes             awesome_northcut
$ 
```

### What is the ID of the container that uses the alpine image and is not running?


```ruby
$ docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                      PORTS     NAMES
a31be71c418a   alpine         "/bin/sh"                7 minutes ago    Exited (0) 7 minutes ago              thirsty_northcutt
$ 
```

### What is the state of the stopped alpine container?
```ruby
$ docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                      PORTS     NAMES
a31be71c418a   alpine         "/bin/sh"                7 minutes ago    ***Exited (0) 7 minutes ago***              thirsty_northcutt
```

### Delete all containers from the Docker Host.


Both Running and Not Running ones. Remember you may have to stop containers before deleting them.

```
To stop containers run the command docker stop <container id | container name>
And then to delete them run docker rm <container id | container name>

To stop all the containers at once, run the command: docker stop $(docker ps -aq)

To remove all the stopped containers at once, run the command: docker rm $(docker ps -aq)`

```

```ruby
$ docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                      PORTS     NAMES
a31be71c418a   alpine         "/bin/sh"                7 minutes ago    Exited (0) 7 minutes ago              thirsty_northcutt
685e98a9dbd8   alpine         "sleep 1000"             7 minutes ago    Up 7 minutes                          vibrant_swirles
10ea03111e51   nginx:alpine   "/docker-entrypoint.…"   7 minutes ago    Up 7 minutes                80/tcp    nginx-2
a70c20dfc8d2   nginx:alpine   "/docker-entrypoint.…"   7 minutes ago    Up 7 minutes                80/tcp    nginx-1
a89b947b7ddf   ubuntu         "sleep 1000"             7 minutes ago    Up 7 minutes                          awesome_northcut
868707999e0a   redis          "docker-entrypoint.s…"   12 minutes ago   Exited (0) 10 minutes ago             stoic_khayyam
$ docker stop $(docker ps -aq)
a31be71c418a
685e98a9dbd8
10ea03111e51
a70c20dfc8d2
a89b947b7ddf
868707999e0a
$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
$ docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                        PORTS     NAMES
a31be71c418a   alpine         "/bin/sh"                12 minutes ago   Exited (0) 12 minutes ago               thirsty_northcutt
685e98a9dbd8   alpine         "sleep 1000"             12 minutes ago   Exited (137) 20 seconds ago             vibrant_swirles
10ea03111e51   nginx:alpine   "/docker-entrypoint.…"   12 minutes ago   Exited (0) 30 seconds ago               nginx-2
a70c20dfc8d2   nginx:alpine   "/docker-entrypoint.…"   12 minutes ago   Exited (0) 30 seconds ago               nginx-1
a89b947b7ddf   ubuntu         "sleep 1000"             12 minutes ago   Exited (137) 20 seconds ago             awesome_northcut
868707999e0a   redis          "docker-entrypoint.s…"   17 minutes ago   Exited (0) 15 minutes ago               stoic_khayyam
$ docker rm $(docker ps -aq)
a31be71c418a
685e98a9dbd8
10ea03111e51
a70c20dfc8d2
a89b947b7ddf
868707999e0a
$ docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
$ 

```

### Delete the ubuntu Image.
```ruby
$ docker rmi ubuntu
Untagged: ubuntu:latest
Untagged: ubuntu@sha256:67211c14fa74f070d27cc59d69a7fa9aeff8e28ea118ef3babc295a0428a6d21
Deleted: sha256:08d22c0ceb150ddeb2237c5fa3129c0183f3cc6f5eeb2e7aa4016da3ad02140a
Deleted: sha256:b93c1bd012ab8fda60f5b4f5906bf244586e0e3292d84571d3abb56472248466
$ docker images
REPOSITORY                      TAG       IMAGE ID       CREATED        SIZE
redis                           latest    eca1379fe8b5   6 months ago   117MB
mysql                           latest    8189e588b0e8   6 months ago   564MB
nginx                           latest    6efc10a0510f   6 months ago   142MB
postgres                        latest    ceccf204404e   6 months ago   379MB
nginx                           alpine    8e75cbc5b25c   6 months ago   41MB
alpine                          latest    9ed4aefc74f6   6 months ago   7.04MB
kodekloud/simple-webapp-mysql   latest    129dd9f67367   5 years ago    96.6MB
kodekloud/simple-webapp         latest    c6e3cd9aae36   5 years ago    84.8MB
$ 
```

### 
```ruby

```

### 
```ruby

```

### 
```ruby

```

### 
```ruby

```

### 
```ruby

```

### 
```ruby

```

### 
```ruby

```

### 
```ruby

```

### 
```ruby

```

### 
```ruby

```

