```ruby
althaf@mas:~$ cat /etc/*release*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=23.04
DISTRIB_CODENAME=lunar
DISTRIB_DESCRIPTION="Ubuntu 23.04"
PRETTY_NAME="Ubuntu 23.04"
NAME="Ubuntu"
VERSION_ID="23.04"
VERSION="23.04 (Lunar Lobster)"
VERSION_CODENAME=lunar
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=lunar
LOGO=ubuntu-logo
althaf@mas:~$ docker ps
CONTAINER ID   IMAGE      COMMAND                  CREATED       STATUS      PORTS                                                 NAMES
ea31344ecd60   postgres   "docker-entrypoint.s…"   10 days ago   Up 3 days   5432/tcp, 0.0.0.0:5434->5434/tcp, :::5434->5434/tcp   django-k8s-postgres_db-1
935762c361a1   redis      "redis-server --appe…"   4 weeks ago   Up 3 days   6379/tcp, 0.0.0.0:6388->6388/tcp, :::6388->6388/tcp   django-k8s-redis_db-1
althaf@mas:~$ docker images
REPOSITORY                                                              TAG       IMAGE ID       CREATED        SIZE
registry.digitalocean.com/mask8s/django-k8s-web                         latest    a64e85378aab   12 days ago    344MB
registry.digitalocean.com/mask8s/django-k8s-web                         v1        a64e85378aab   12 days ago    344MB
registry.digitalocean.com/mask8s/django-k8s-web                         <none>    d0f781bb0396   12 days ago    344MB
registry.digitalocean.com/mask8s/django-k8s-web                         <none>    09c53916567b   3 weeks ago    344MB
registry.digitalocean.com/mask8s/django-k8s                             latest    0cfdecabe1b0   3 weeks ago    344MB
registry.digitalocean.com/registry.digitalocean.com/mask8s/django-k8s   latest    0cfdecabe1b0   3 weeks ago    344MB
django-k8s                                                              v1        19fd2726d206   4 weeks ago    344MB
<none>                                                                  <none>    83b4b2ce10f6   4 weeks ago    344MB
<none>                                                                  <none>    856a5df52c93   4 weeks ago    344MB
<none>                                                                  <none>    c4b211b9eb69   4 weeks ago    344MB
<none>                                                                  <none>    f640353b9484   4 weeks ago    344MB
<none>                                                                  <none>    cc2133a76061   4 weeks ago    344MB
<none>                                                                  <none>    bedc60b6a120   4 weeks ago    344MB
<none>                                                                  <none>    eec261bddbd5   4 weeks ago    344MB
<none>                                                                  <none>    5032273b353f   4 weeks ago    344MB
<none>                                                                  <none>    8271f435c159   4 weeks ago    344MB
<none>                                                                  <none>    d2a04d84b0a6   4 weeks ago    344MB
<none>                                                                  <none>    90071b01ef17   4 weeks ago    344MB
<none>                                                                  <none>    bfb5bd06e9a7   4 weeks ago    344MB
<none>                                                                  <none>    2b37e5c00ca9   4 weeks ago    344MB
<none>                                                                  <none>    6e2b3190c635   4 weeks ago    344MB
postgres                                                                latest    a373cbdcfe8b   4 weeks ago    418MB
redis                                                                   latest    39ac5829bade   6 weeks ago    138MB
alpine                                                                  latest    7e01a0d0a1dc   2 months ago   7.34MB
gcr.io/k8s-minikube/kicbase                                             v0.0.40   c6cc01e60919   3 months ago   1.19GB
hello-world                                                             latest    9c7a54a9a43c   5 months ago   13.3kB
althaf@mas:~$ docker rm 83 85
Error response from daemon: No such container: 83
Error response from daemon: No such container: 85
althaf@mas:~$ docker rm 9c
Error response from daemon: No such container: 9c
althaf@mas:~$ docker rmi hello-world
Error response from daemon: conflict: unable to remove repository reference "hello-world" (must force) - container 35a4186b57b5 is using its referenced image 9c7a54a9a43c
althaf@mas:~$ docker ps -a
CONTAINER ID   IMAGE                                 COMMAND                  CREATED       STATUS                     PORTS                                                                                                                                  NAMES
ea31344ecd60   postgres                              "docker-entrypoint.s…"   10 days ago   Up 3 days                  5432/tcp, 0.0.0.0:5434->5434/tcp, :::5434->5434/tcp                                                                                    django-k8s-postgres_db-1
60cfb35bf6bf   gcr.io/k8s-minikube/kicbase:v0.0.40   "/usr/local/bin/entr…"   4 weeks ago   Exited (255) 4 weeks ago   127.0.0.1:32772->22/tcp, 127.0.0.1:32771->2376/tcp, 127.0.0.1:32770->5000/tcp, 127.0.0.1:32769->8443/tcp, 127.0.0.1:32768->32443/tcp   minikube
935762c361a1   redis                                 "redis-server --appe…"   4 weeks ago   Up 3 days                  6379/tcp, 0.0.0.0:6388->6388/tcp, :::6388->6388/tcp                                                                                    django-k8s-redis_db-1
fff9f021369b   django-k8s:v1                         "sh -c 'chmod +x /ap…"   4 weeks ago   Exited (137) 4 weeks ago                                                                                                                                          django-k8s-web-1
1ea1500bf471   alpine                                "/bin/sh"                4 weeks ago   Exited (137) 4 weeks ago                                                                                                                                          ohyeah
1e1b99cd1e11   hello-world                           "/hello"                 4 weeks ago   Exited (0) 4 weeks ago                                                                                                                                            flamboyant_meninsky
6e1abd78a400   hello-world                           "/hello"                 4 weeks ago   Exited (0) 4 weeks ago                                                                                                                                            peaceful_golick
35a4186b57b5   hello-world                           "/hello"                 4 weeks ago   Exited (0) 4 weeks ago                                                                                                                                            practical_agnesi
565a86d19151   hello-world                           "/hello"                 4 weeks ago   Exited (0) 4 weeks ago                                                                                                                                            relaxed_williamson
althaf@mas:~$ docker stop 56 35 6e 1e1 
56
35
6e
1e1
althaf@mas:~$ docker ps -a
CONTAINER ID   IMAGE                                 COMMAND                  CREATED       STATUS                     PORTS                                                                                                                                  NAMES
ea31344ecd60   postgres                              "docker-entrypoint.s…"   10 days ago   Up 3 days                  5432/tcp, 0.0.0.0:5434->5434/tcp, :::5434->5434/tcp                                                                                    django-k8s-postgres_db-1
60cfb35bf6bf   gcr.io/k8s-minikube/kicbase:v0.0.40   "/usr/local/bin/entr…"   4 weeks ago   Exited (255) 4 weeks ago   127.0.0.1:32772->22/tcp, 127.0.0.1:32771->2376/tcp, 127.0.0.1:32770->5000/tcp, 127.0.0.1:32769->8443/tcp, 127.0.0.1:32768->32443/tcp   minikube
935762c361a1   redis                                 "redis-server --appe…"   4 weeks ago   Up 3 days                  6379/tcp, 0.0.0.0:6388->6388/tcp, :::6388->6388/tcp                                                                                    django-k8s-redis_db-1
fff9f021369b   django-k8s:v1                         "sh -c 'chmod +x /ap…"   4 weeks ago   Exited (137) 4 weeks ago                                                                                                                                          django-k8s-web-1
1ea1500bf471   alpine                                "/bin/sh"                4 weeks ago   Exited (137) 4 weeks ago                                                                                                                                          ohyeah
1e1b99cd1e11   hello-world                           "/hello"                 4 weeks ago   Exited (0) 4 weeks ago                                                                                                                                            flamboyant_meninsky
6e1abd78a400   hello-world                           "/hello"                 4 weeks ago   Exited (0) 4 weeks ago                                                                                                                                            peaceful_golick
35a4186b57b5   hello-world                           "/hello"                 4 weeks ago   Exited (0) 4 weeks ago                                                                                                                                            practical_agnesi
565a86d19151   hello-world                           "/hello"                 4 weeks ago   Exited (0) 4 weeks ago                                                                                                                                            relaxed_williamson
althaf@mas:~$ docker rm 565a86d19151
565a86d19151
althaf@mas:~$ docker ps -a
CONTAINER ID   IMAGE                                 COMMAND                  CREATED       STATUS                     PORTS                                                                                                                                  NAMES
ea31344ecd60   postgres                              "docker-entrypoint.s…"   10 days ago   Up 3 days                  5432/tcp, 0.0.0.0:5434->5434/tcp, :::5434->5434/tcp                                                                                    django-k8s-postgres_db-1
60cfb35bf6bf   gcr.io/k8s-minikube/kicbase:v0.0.40   "/usr/local/bin/entr…"   4 weeks ago   Exited (255) 4 weeks ago   127.0.0.1:32772->22/tcp, 127.0.0.1:32771->2376/tcp, 127.0.0.1:32770->5000/tcp, 127.0.0.1:32769->8443/tcp, 127.0.0.1:32768->32443/tcp   minikube
935762c361a1   redis                                 "redis-server --appe…"   4 weeks ago   Up 3 days                  6379/tcp, 0.0.0.0:6388->6388/tcp, :::6388->6388/tcp                                                                                    django-k8s-redis_db-1
fff9f021369b   django-k8s:v1                         "sh -c 'chmod +x /ap…"   4 weeks ago   Exited (137) 4 weeks ago                                                                                                                                          django-k8s-web-1
1ea1500bf471   alpine                                "/bin/sh"                4 weeks ago   Exited (137) 4 weeks ago                                                                                                                                          ohyeah
1e1b99cd1e11   hello-world                           "/hello"                 4 weeks ago   Exited (0) 4 weeks ago                                                                                                                                            flamboyant_meninsky
6e1abd78a400   hello-world                           "/hello"                 4 weeks ago   Exited (0) 4 weeks ago                                                                                                                                            peaceful_golick
35a4186b57b5   hello-world                           "/hello"                 4 weeks ago   Exited (0) 4 weeks ago                                                                                                                                            practical_agnesi
althaf@mas:~$ docker rm 35a4186b57b5
35a4186b57b5
althaf@mas:~$ docker rm 6e1abd78a400 1e1b99cd1e11
6e1abd78a400
1e1b99cd1e11
althaf@mas:~$ docker ps -a
CONTAINER ID   IMAGE                                 COMMAND                  CREATED       STATUS                     PORTS                                                                                                                                  NAMES
ea31344ecd60   postgres                              "docker-entrypoint.s…"   10 days ago   Up 3 days                  5432/tcp, 0.0.0.0:5434->5434/tcp, :::5434->5434/tcp                                                                                    django-k8s-postgres_db-1
60cfb35bf6bf   gcr.io/k8s-minikube/kicbase:v0.0.40   "/usr/local/bin/entr…"   4 weeks ago   Exited (255) 4 weeks ago   127.0.0.1:32772->22/tcp, 127.0.0.1:32771->2376/tcp, 127.0.0.1:32770->5000/tcp, 127.0.0.1:32769->8443/tcp, 127.0.0.1:32768->32443/tcp   minikube
935762c361a1   redis                                 "redis-server --appe…"   4 weeks ago   Up 3 days                  6379/tcp, 0.0.0.0:6388->6388/tcp, :::6388->6388/tcp                                                                                    django-k8s-redis_db-1
fff9f021369b   django-k8s:v1                         "sh -c 'chmod +x /ap…"   4 weeks ago   Exited (137) 4 weeks ago                                                                                                                                          django-k8s-web-1
1ea1500bf471   alpine                                "/bin/sh"                4 weeks ago   Exited (137) 4 weeks ago                                                                                                                                          ohyeah
althaf@mas:~$ docker rm 1ea1500bf471
1ea1500bf471
althaf@mas:~$ docker images
REPOSITORY                                                              TAG       IMAGE ID       CREATED        SIZE
registry.digitalocean.com/mask8s/django-k8s-web                         latest    a64e85378aab   12 days ago    344MB
registry.digitalocean.com/mask8s/django-k8s-web                         v1        a64e85378aab   12 days ago    344MB
registry.digitalocean.com/mask8s/django-k8s-web                         <none>    d0f781bb0396   12 days ago    344MB
registry.digitalocean.com/mask8s/django-k8s-web                         <none>    09c53916567b   3 weeks ago    344MB
registry.digitalocean.com/mask8s/django-k8s                             latest    0cfdecabe1b0   3 weeks ago    344MB
registry.digitalocean.com/registry.digitalocean.com/mask8s/django-k8s   latest    0cfdecabe1b0   3 weeks ago    344MB
django-k8s                                                              v1        19fd2726d206   4 weeks ago    344MB
<none>                                                                  <none>    83b4b2ce10f6   4 weeks ago    344MB
<none>                                                                  <none>    856a5df52c93   4 weeks ago    344MB
<none>                                                                  <none>    c4b211b9eb69   4 weeks ago    344MB
<none>                                                                  <none>    f640353b9484   4 weeks ago    344MB
<none>                                                                  <none>    cc2133a76061   4 weeks ago    344MB
<none>                                                                  <none>    bedc60b6a120   4 weeks ago    344MB
<none>                                                                  <none>    eec261bddbd5   4 weeks ago    344MB
<none>                                                                  <none>    5032273b353f   4 weeks ago    344MB
<none>                                                                  <none>    8271f435c159   4 weeks ago    344MB
<none>                                                                  <none>    d2a04d84b0a6   4 weeks ago    344MB
<none>                                                                  <none>    90071b01ef17   4 weeks ago    344MB
<none>                                                                  <none>    bfb5bd06e9a7   4 weeks ago    344MB
<none>                                                                  <none>    2b37e5c00ca9   4 weeks ago    344MB
<none>                                                                  <none>    6e2b3190c635   4 weeks ago    344MB
postgres                                                                latest    a373cbdcfe8b   4 weeks ago    418MB
redis                                                                   latest    39ac5829bade   6 weeks ago    138MB
alpine                                                                  latest    7e01a0d0a1dc   2 months ago   7.34MB
gcr.io/k8s-minikube/kicbase                                             v0.0.40   c6cc01e60919   3 months ago   1.19GB
hello-world                                                             latest    9c7a54a9a43c   5 months ago   13.3kB
althaf@mas:~$ docker rmi 83b4b2ce10f6 856a5df52c93
Deleted: sha256:83b4b2ce10f6d51a734be2db42e66aa5354541c488a73add7e1a1a1156be8213
Deleted: sha256:856a5df52c93a52629543dbdb0461d58a731c06f466b87ca0603a98e4a7ee199
althaf@mas:~$ docker rmi c4b211b9eb69 f640353b9484 cc2133a76061 bedc60b6a120 5032273b353f
Deleted: sha256:c4b211b9eb69cd2c92af7b1528e7ca75b28bb2dfeefa324758f92dfd9f96fdee
Deleted: sha256:f640353b948418bf0df4f6bb3c5ee980d090fb8684540c608e7f1ef2ee4a02fb
Deleted: sha256:cc2133a76061f1c8cfdd21b8da724553d4039c9fc4459c34ff4848ad684033ba
Deleted: sha256:bedc60b6a120ff64f90331712afc3eac08271972d6ecfc6ebf322cf0fc653053
Deleted: sha256:5032273b353ff6bae0d3a84e9f073b5b1d0f63685014eb9c361285ff3ec9944f
althaf@mas:~$ docker images
REPOSITORY                                                              TAG       IMAGE ID       CREATED        SIZE
registry.digitalocean.com/mask8s/django-k8s-web                         latest    a64e85378aab   12 days ago    344MB
registry.digitalocean.com/mask8s/django-k8s-web                         v1        a64e85378aab   12 days ago    344MB
registry.digitalocean.com/mask8s/django-k8s-web                         <none>    d0f781bb0396   12 days ago    344MB
registry.digitalocean.com/mask8s/django-k8s-web                         <none>    09c53916567b   3 weeks ago    344MB
registry.digitalocean.com/mask8s/django-k8s                             latest    0cfdecabe1b0   3 weeks ago    344MB
registry.digitalocean.com/registry.digitalocean.com/mask8s/django-k8s   latest    0cfdecabe1b0   3 weeks ago    344MB
django-k8s                                                              v1        19fd2726d206   4 weeks ago    344MB
<none>                                                                  <none>    eec261bddbd5   4 weeks ago    344MB
<none>                                                                  <none>    8271f435c159   4 weeks ago    344MB
<none>                                                                  <none>    d2a04d84b0a6   4 weeks ago    344MB
<none>                                                                  <none>    90071b01ef17   4 weeks ago    344MB
<none>                                                                  <none>    bfb5bd06e9a7   4 weeks ago    344MB
<none>                                                                  <none>    2b37e5c00ca9   4 weeks ago    344MB
<none>                                                                  <none>    6e2b3190c635   4 weeks ago    344MB
postgres                                                                latest    a373cbdcfe8b   4 weeks ago    418MB
redis                                                                   latest    39ac5829bade   6 weeks ago    138MB
alpine                                                                  latest    7e01a0d0a1dc   2 months ago   7.34MB
gcr.io/k8s-minikube/kicbase                                             v0.0.40   c6cc01e60919   3 months ago   1.19GB
hello-world                                                             latest    9c7a54a9a43c   5 months ago   13.3kB
althaf@mas:~$ docker rmi eec261bddbd5 8271f435c159 d2a04d84b0a6 90071b01ef17 bfb5bd06e9a7 2b37e5c00ca9 2b37e5c00ca9 6e2b3190c635
Deleted: sha256:eec261bddbd5ea16d3d3c76f9d7283b46f58796e12834d4c0e929e53f38a3e8b
Deleted: sha256:8271f435c159e311fefbc2f33f9702195dc0b44c8d56208bdf5101c4b1f7572c
Deleted: sha256:d2a04d84b0a6417f425eb116c05c3d0d2fa7509a1245c26983269dc74defd1fc
Deleted: sha256:90071b01ef170ed79f3a16975169f1abd07f07c702ee7f584048974b031ae514
Deleted: sha256:bfb5bd06e9a750f430531dd98f996276461f7f58061766a97404f5b6eee93984
Deleted: sha256:2b37e5c00ca9b5041c927727bcc4c58c2515163a6421d251b64ca371758bc4e0
Deleted: sha256:6e2b3190c635a567767d48ed763357d56945058d8a8310a67e9443312e379b1e
Error response from daemon: No such image: 2b37e5c00ca9:latest
althaf@mas:~$ docker images
REPOSITORY                                                              TAG       IMAGE ID       CREATED        SIZE
registry.digitalocean.com/mask8s/django-k8s-web                         latest    a64e85378aab   12 days ago    344MB
registry.digitalocean.com/mask8s/django-k8s-web                         v1        a64e85378aab   12 days ago    344MB
registry.digitalocean.com/mask8s/django-k8s-web                         <none>    d0f781bb0396   12 days ago    344MB
registry.digitalocean.com/mask8s/django-k8s-web                         <none>    09c53916567b   3 weeks ago    344MB
registry.digitalocean.com/mask8s/django-k8s                             latest    0cfdecabe1b0   3 weeks ago    344MB
registry.digitalocean.com/registry.digitalocean.com/mask8s/django-k8s   latest    0cfdecabe1b0   3 weeks ago    344MB
django-k8s                                                              v1        19fd2726d206   4 weeks ago    344MB
postgres                                                                latest    a373cbdcfe8b   4 weeks ago    418MB
redis                                                                   latest    39ac5829bade   6 weeks ago    138MB
alpine                                                                  latest    7e01a0d0a1dc   2 months ago   7.34MB
gcr.io/k8s-minikube/kicbase                                             v0.0.40   c6cc01e60919   3 months ago   1.19GB
hello-world                                                             latest    9c7a54a9a43c   5 months ago   13.3kB
althaf@mas:~$ docker ps
CONTAINER ID   IMAGE      COMMAND                  CREATED       STATUS      PORTS                                                 NAMES
ea31344ecd60   postgres   "docker-entrypoint.s…"   10 days ago   Up 3 days   5432/tcp, 0.0.0.0:5434->5434/tcp, :::5434->5434/tcp   django-k8s-postgres_db-1
935762c361a1   redis      "redis-server --appe…"   4 weeks ago   Up 3 days   6379/tcp, 0.0.0.0:6388->6388/tcp, :::6388->6388/tcp   django-k8s-redis_db-1
althaf@mas:~$ docker ps -a
CONTAINER ID   IMAGE                                 COMMAND                  CREATED       STATUS                     PORTS                                                                                                                                  NAMES
ea31344ecd60   postgres                              "docker-entrypoint.s…"   10 days ago   Up 3 days                  5432/tcp, 0.0.0.0:5434->5434/tcp, :::5434->5434/tcp                                                                                    django-k8s-postgres_db-1
60cfb35bf6bf   gcr.io/k8s-minikube/kicbase:v0.0.40   "/usr/local/bin/entr…"   4 weeks ago   Exited (255) 4 weeks ago   127.0.0.1:32772->22/tcp, 127.0.0.1:32771->2376/tcp, 127.0.0.1:32770->5000/tcp, 127.0.0.1:32769->8443/tcp, 127.0.0.1:32768->32443/tcp   minikube
935762c361a1   redis                                 "redis-server --appe…"   4 weeks ago   Up 3 days                  6379/tcp, 0.0.0.0:6388->6388/tcp, :::6388->6388/tcp                                                                                    django-k8s-redis_db-1
fff9f021369b   django-k8s:v1                         "sh -c 'chmod +x /ap…"   4 weeks ago   Exited (137) 4 weeks ago                                                                                                                                          django-k8s-web-1
althaf@mas:~$ 

```
