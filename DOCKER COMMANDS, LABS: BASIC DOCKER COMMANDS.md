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

### You are required to pull a docker image which will be used to run a container later. Pull the image nginx:1.14-alpine


Only pull the image, do not create a container.

```ruby
$ docker pull nginx:1.14-alpine
1.14-alpine: Pulling from library/nginx
bdf0201b3a05: Pull complete 
3d0a573c81ed: Pull complete 
8129faeb2eb6: Pull complete 
3dc99f571daf: Pull complete 
Digest: sha256:485b610fefec7ff6c463ced9623314a04ed67e3945b9c08d7e53a47f6d108dc7
Status: Downloaded newer image for nginx:1.14-alpine
docker.io/library/nginx:1.14-alpine
$ 
```

### Run a container with the nginx:1.14-alpine image and name it webapp
```ruby
$ docker run -d --name webapp nginx:1.14-alpine
2a8562465f9fe3d794b487594d49928a1cd4a1e237e64ad5e2abe06e48cbe3bb
$ docker ps
CONTAINER ID   IMAGE               COMMAND                  CREATED         STATUS         PORTS     NAMES
2a8562465f9f   nginx:1.14-alpine   "nginx -g 'daemon of…"   8 seconds ago   Up 6 seconds   80/tcp    webapp
$ 
```

### Cleanup: Delete all images on the host


Remove containers as necessary

```
Stop and delete all the containers being used by images.

Then run the command to delete all the available images: docker rmi $(docker images -aq)
```

```ruby
$ docker ps
CONTAINER ID   IMAGE               COMMAND                  CREATED         STATUS         PORTS     NAMES
2a8562465f9f   nginx:1.14-alpine   "nginx -g 'daemon of…"   2 minutes ago   Up 2 minutes   80/tcp    webapp
$ docker rm 2a8562465f9f
Error response from daemon: You cannot remove a running container 2a8562465f9fe3d794b487594d49928a1cd4a1e237e64ad5e2abe06e48cbe3bb. Stop the container before attempting removal or force remove
$ docker stop 2a8562465f9f
2a8562465f9f
$ docker rm 2a8562465f9f
2a8562465f9f
$ docker rmi $(docker images -aq)
Untagged: redis:latest
Untagged: redis@sha256:f50031a49f41e493087fb95f96fdb3523bb25dcf6a3f0b07c588ad3cdbe1d0aa
Deleted: sha256:eca1379fe8b541831fd5ce4a252c263db0cef4efbfd428a94225dc020aaeb1af
Deleted: sha256:21acda8c08f1a6109e2fb61ed010d368ee6581cf30128cdaab0e6b91dabffc22
Deleted: sha256:aafc83c9f9299ba7a3af08ab0b1f822340278803714695fd2a96351fe89b37ea
Deleted: sha256:644ab96acc6e4232dc7be6f1855b27f5f3534b17b9e9c19ae2557991b99487db
Deleted: sha256:6e75f4867056adfca8dfafbb0e94a525064797e4f0a106bca817b5afce47af73
Deleted: sha256:84e4c46eefa83bc327e4e356365ec03a3ee1f691d181235e5b69e36663f7dd57
Untagged: mysql:latest
Untagged: mysql@sha256:a43f6e7e7f3a5e5b90f857fbed4e3103ece771b19f0f75880f767cf66bbb6577
Deleted: sha256:8189e588b0e8fcc95b0d764d6f7bdb55b5b41e9249157177d73781058f603ca9
Deleted: sha256:48c450c06ed83938e899fb0b77b2e9e35094015b503bb5e88de6c2d93f445241
Deleted: sha256:c5d77efb49ec3a7a74ab898b9da9217ec78fa9bee47018409025467611d60329
Deleted: sha256:de0c00e28b37cc33347f02709e0a6a2f17637b1e761fb96616861ed345bd34f6
Deleted: sha256:cc635684e233946f93fe008e0322c86e15cbb97b56c58d269a5f8f9da15d973d
Deleted: sha256:0b795b85d567512d79a544b1b74f21108339156cbbc78d16921e96a2a69f687b
Deleted: sha256:16e250c36f4c0e1085512653edd47fd03b60d230ddb575aabc8eb224d96e668f
Deleted: sha256:d023b92a46a5fa8fa8d54387e6d3cb0c73997fefc64ec9000eab0ee1c550ef45
Deleted: sha256:f1c1643119168a94089eab1c9126cda0ee6056a4bb4b18e27a7dcacdf4823972
Deleted: sha256:b147319dd21e8994e6d2fb3bb58a8278c5a72f39488e1f1cff94fc73f1089eb9
Deleted: sha256:ff7c2b28c0dfaa63d0d30b7a5069bf526b0f6492143110381351bbf7d07b4baf
Deleted: sha256:caefa4e45110eab274ebbdbc781f9227229f947f8718cee62ebeff1aac8f1d5b
Untagged: nginx:latest
Untagged: nginx@sha256:63b44e8ddb83d5dd8020327c1f40436e37a6fffd3ef2498a6204df23be6e7e94
Deleted: sha256:6efc10a0510f143a90b69dc564a914574973223e88418d65c1f8809e08dc0a1f
Deleted: sha256:a489ce38666d5aff5d73930d115381b154a503b48c5534357d5183160f5b9bfa
Deleted: sha256:ce2a611250a8bb55b73959de5865489d566bf48e1342c74b46b107e9a224370e
Deleted: sha256:fa6c51798227fd451cc3ff628c46c1b62c0d1d08e43374be7000c78ad910c0c0
Deleted: sha256:c426467d564c8684df87356eb045dc50d8b5af9521e9775c1b6bb941135680de
Deleted: sha256:c6deada06ccd386201e5b95c38e19297cd3eeb5264d6413d9cc7441020816401
Untagged: postgres:latest
Untagged: postgres@sha256:6cc97262444f1c45171081bc5a1d4c28b883ea46a6e0d1a45a8eac4a7f4767ab
Deleted: sha256:ceccf204404e5efe764f2d4d97e6977db04062579d525d9cb445cf93e0f0fef4
Deleted: sha256:5581e2a0252cdb4f2b1847cfd9300122841787cd0a9ba13e095425b22c08bb05
Deleted: sha256:b8d9a959ce0f6039bf4061ddedb320c05b9b049b5bd8dabb2b5f9d697fdc4e0e
Deleted: sha256:d426781ae8413908a52d86fb8f28319b834625c5c6b194e3d122d1b1eb179d87
Deleted: sha256:ee6f16055bfd3ad8bcc92a9af3567c69c0bb499cbc2c2b9a2f2ccafa3538504b
Deleted: sha256:42c973890245849bff76e03def91ceacb87da92a19fa5aa7eab58975a811c683
Deleted: sha256:179015cc5c69fea24583ca7a52a8ba75dd363310d17461b6eb9b430c0d69a37e
Deleted: sha256:9362c3f758a9916eb7e2262af8e63d7f1b0a45818e7ac033c9152ecf049933d0
Deleted: sha256:b47ed6c8bc9fa1548ed586316aa7a0e27b34937efb1b3c4ad5742ae3a5d63f8c
Deleted: sha256:a603ddfeb1e19bb984a56b96e96cc987d8e27621390a9bc1b11f7003ff357e7d
Deleted: sha256:ca073f3da5fc959ed40fff93ae9a550ddb14916b3f8bd620235d306f5e9d3d64
Deleted: sha256:fd2d7bb88deba0351caf0ee032dac84272a04e489fd055407cddd740009e329c
Deleted: sha256:2c3cc0e91a94c04e5446f3a8061970073053850ce8093a46ba819b8e59af1dee
Deleted: sha256:ed7b0ef3bf5bbec74379c3ae3d5339e666a314223e863c70644f7522a7527461
Untagged: nginx:alpine
Untagged: nginx@sha256:dd2a9179765849767b10e2adde7e10c4ad6b7e4d4846e6b77ec93f080cd2db27
Deleted: sha256:8e75cbc5b25c8438fcfe2e7c12c98409d5f161cbb668d6c444e02796691ada70
Deleted: sha256:f301a4112756ab559d9c78e8ed3625dab81f91803dfeabbc4f9184c878b1f3b1
Deleted: sha256:d794631f2dea08ec92bc28f93ac8c1079c505aef791e86cc2bd5566904d2d581
Deleted: sha256:0d2f2fd89d17527e0808abf8debc4d22c1b3670894eeb12ecee580fe05719dec
Deleted: sha256:13ec71ce1944eb1de9f7fe3bbee31e4355476075b70f8b395a68d90ca849f111
Deleted: sha256:8997729a28eb948a9a00aa56b19143cff03e0ced25280473fff15c461860dfa7
Deleted: sha256:193b9708a46833ccb84791d3d58bf0d5428c37fc8fd80c951d3ca15cca5091c6
Untagged: alpine:latest
Untagged: alpine@sha256:124c7d2707904eea7431fffe91522a01e5a861a624ee31d03372cc1d138a3126
Deleted: sha256:9ed4aefc74f6792b5a804d1d146fe4b4a2299147b0f50eaf2b08435d7b38c27e
Deleted: sha256:f1417ff83b319fbdae6dd9cd6d8c9c88002dcd75ecf6ec201c8c6894681cf2b5
Untagged: nginx:1.14-alpine
Untagged: nginx@sha256:485b610fefec7ff6c463ced9623314a04ed67e3945b9c08d7e53a47f6d108dc7
Deleted: sha256:8a2fb25a19f5dc1528b7a3fabe8b3145ff57fe10e4f1edac6c718a3cf4aa4b73
Deleted: sha256:f68a8bcb9dbd06e0d2750eabf63c45f51734a72831ed650d2349775865d5fc20
Deleted: sha256:cbf2c7789332fe231e8defa490527a7b2c3ae8589997ceee00895f3263f0a8cf
Deleted: sha256:894f3fad7e6ecd7f24e88340a44b7b73663a85c0eb7740e7ade169e9d8491a4c
Deleted: sha256:a464c54f93a9e88fc1d33df1e0e39cca427d60145a360962e8f19a1dbf900da9
Untagged: kodekloud/simple-webapp-mysql:latest
Untagged: kodekloud/simple-webapp-mysql@sha256:92943d2b3ea4a1db7c8a9529cd5786ae3b9999e0246ab665c29922e9800d1b41
Deleted: sha256:129dd9f673673e9e8507ac837dcd9eaa3906469c10ef4aa63d0cac1f1dfa6b3a
Deleted: sha256:07711c2005c750fa9c42f5667ec657d7f5126f710915cf917cf5c0e9e3871242
Deleted: sha256:69dbe0a61b055e5e63706bc76a875220e02769e880d1846c6f965c2f4b1b1dfe
Deleted: sha256:5978a6831cce81b23e657b11150010eb8acf463a183cbe540eb6c769314a0f8a
Deleted: sha256:93099f51e789a3d87e77501591ab260ca2ff9b8532a78f9fc6bebaa2d5ffcad4
Deleted: sha256:15df614f20bc13c6da75c43616dec28d17908970491a562820fabbc11a1e562c
Deleted: sha256:a8dc474c5cce41198ea9a334a54bd7d59043f86c32c3b8e3f0d76a52adf09cf2
Deleted: sha256:362e5432c5954e9f081657f369b00d821cecd10274b8885f1d6fd1b2e8c1a405
Deleted: sha256:73046094a9b835e443af1a9d736fcfc11a994107500e474d0abf399499ed280c
Untagged: kodekloud/simple-webapp:latest
Untagged: kodekloud/simple-webapp@sha256:e5355b4c7804f453d79de75d6659ee702eeebbe30c02d9f1ce6602a96b576e57
Deleted: sha256:c6e3cd9aae3645a98dd69c15b048614603efce6cda26c60f5f7e867ef68f729f
Deleted: sha256:33833b97952fc68d999bc3bccaad23687ea6a939724e0130c151dc973ba8f2d3
Deleted: sha256:a3dd002bb33a1cdb83aface983ea0d268be1b4ffda0e42ce72aa5c22ced6701f
Deleted: sha256:12e8c893d121075ced84d32b967f6de75ff67e1cf7c9b66b63636bdf630ac12c
Deleted: sha256:4785d1dd03a24d6b30c9342db24ac2254d01362e7f3b3f28f55a00e4858f85e5
Deleted: sha256:9de207c08e3d729c3b9c451d87e109144cdc6e2e71f4fcad80c9cbf99879d8bb
Deleted: sha256:0a2679c979afc5eb30764613ae1fa22199b872610f709f556b9f35bc0717e3f1
Deleted: sha256:df64d3292fd6194b7865d7326af5255db6d81e9df29f48adde61a918fbd8c332
$ docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
$ docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
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

