# Pull the Jenkins image from docker hub  and Run


```ruby
althaf@mas:~$ docker pull jenkins/jenkins
Using default tag: latest
latest: Pulling from jenkins/jenkins
0a9573503463: Pull complete 
1cdc1811baee: Pull complete 
3fa5e8773761: Pull complete 
3650dd122ffb: Pull complete 
66f00e939517: Pull complete 
c5c89718f699: Pull complete 
b4b31f4a2810: Pull complete 
bf15702f2535: Pull complete 
4a9169297eb5: Pull complete 
1cb861394516: Pull complete 
249f2d1f9ad5: Pull complete 
fb002adb1777: Pull complete 
Digest: sha256:b728c15f3d9aa442b9ab5d6d6e75f2e5663e4a14f22dfcdac35f83245e76b343
Status: Downloaded newer image for jenkins/jenkins:latest
docker.io/jenkins/jenkins:latest
```
# Run the image

```ruby
althaf@mas:~$ docker run jenkins/jenkins
Running from: /usr/share/jenkins/jenkins.war
webroot: /var/jenkins_home/war
2023-10-20 07:20:27.065+0000 [id=1]	INFO	winstone.Logger#logInternal: Beginning extraction from war file
2023-10-20 07:20:27.625+0000 [id=1]	WARNING	o.e.j.s.handler.ContextHandler#setContextPath: Empty contextPath
2023-10-20 07:20:27.680+0000 [id=1]	INFO	org.eclipse.jetty.server.Server#doStart: jetty-10.0.17; built: 2023-10-02T04:04:10.314Z; git: a0f5f05abaa6c3aabb7c3d35f10a6f412ab8b05f; jvm 17.0.8.1+1
2023-10-20 07:20:27.872+0000 [id=1]	INFO	o.e.j.w.StandardDescriptorProcessor#visitServlet: NO JSP Support for /, did not find org.eclipse.jetty.jsp.JettyJspServlet
2023-10-20 07:20:27.913+0000 [id=1]	INFO	o.e.j.s.s.DefaultSessionIdManager#doStart: Session workerName=node0
2023-10-20 07:20:28.360+0000 [id=1]	INFO	hudson.WebAppMain#contextInitialized: Jenkins home directory: /var/jenkins_home found at: EnvVars.masterEnvVars.get("JENKINS_HOME")
2023-10-20 07:20:28.462+0000 [id=1]	INFO	o.e.j.s.handler.ContextHandler#doStart: Started w.@4d8286c4{Jenkins v2.428,/,file:///var/jenkins_home/war/,AVAILABLE}{/var/jenkins_home/war}
2023-10-20 07:20:28.474+0000 [id=1]	INFO	o.e.j.server.AbstractConnector#doStart: Started ServerConnector@37ddb69a{HTTP/1.1, (http/1.1)}{0.0.0.0:8080}
2023-10-20 07:20:28.483+0000 [id=1]	INFO	org.eclipse.jetty.server.Server#doStart: Started Server@43aaf813{STARTING}[10.0.17,sto=0] @1823ms
2023-10-20 07:20:28.484+0000 [id=27]	INFO	winstone.Logger#logInternal: Winstone Servlet Engine running: controlPort=disabled
2023-10-20 07:20:28.670+0000 [id=35]	INFO	jenkins.InitReactorRunner$1#onAttained: Started initialization
2023-10-20 07:20:28.689+0000 [id=41]	INFO	jenkins.InitReactorRunner$1#onAttained: Listed all plugins
2023-10-20 07:20:29.381+0000 [id=46]	INFO	jenkins.InitReactorRunner$1#onAttained: Prepared all plugins
2023-10-20 07:20:29.385+0000 [id=46]	INFO	jenkins.InitReactorRunner$1#onAttained: Started all plugins
2023-10-20 07:20:29.393+0000 [id=39]	INFO	jenkins.InitReactorRunner$1#onAttained: Augmented all extensions
2023-10-20 07:20:29.568+0000 [id=38]	INFO	jenkins.InitReactorRunner$1#onAttained: System config loaded
2023-10-20 07:20:29.568+0000 [id=44]	INFO	jenkins.InitReactorRunner$1#onAttained: System config adapted
2023-10-20 07:20:29.569+0000 [id=44]	INFO	jenkins.InitReactorRunner$1#onAttained: Loaded all jobs
2023-10-20 07:20:29.571+0000 [id=44]	INFO	jenkins.InitReactorRunner$1#onAttained: Configuration for all jobs updated
2023-10-20 07:20:29.597+0000 [id=61]	INFO	hudson.util.Retrier#start: Attempt #1 to do the action check updates server
2023-10-20 07:20:29.895+0000 [id=43]	INFO	jenkins.install.SetupWizard#init: 

*************************************************************
*************************************************************
*************************************************************

Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

77d7ced267ca4bd5957afae331639a13

This may also be found at: /var/jenkins_home/secrets/initialAdminPassword

*************************************************************
*************************************************************
*************************************************************

2023-10-20 07:20:58.900+0000 [id=36]	INFO	jenkins.InitReactorRunner$1#onAttained: Completed initialization
2023-10-20 07:20:58.920+0000 [id=26]	INFO	hudson.lifecycle.Lifecycle#onReady: Jenkins is fully up and running
2023-10-20 07:21:00.630+0000 [id=61]	INFO	h.m.DownloadService$Downloadable#load: Obtained the updated data file for hudson.tasks.Maven.MavenInstaller
2023-10-20 07:21:00.630+0000 [id=61]	INFO	hudson.util.Retrier#start: Performed the action check updates server successfully at the attempt #1

```
### then you can acces via two method 
### 1 .Port mapping
### 2.internal ip

### to chek the internal ip 
```ruby
docker inspect <CONTAINER ID>
```

```ruby
"NetworkSettings": {
            "Bridge": "",
            "SandboxID": "07684fae1d9f04a71ca06c953a711919610aff81f3af720d947da1b46b7386a3",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {
                "50000/tcp": null,
                "8080/tcp": null
            },
            "SandboxKey": "/var/run/docker/netns/07684fae1d9f",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "f7f26e59f33ac5259eeb8a1db241013bc41e9ba5bc2fd74aca12b581b3d7596a",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "9139b1e3e9c2094b900f3dec66bf7a91e315529316ef82c732eeb7cd919eb51b",
                    "EndpointID": "f7f26e59f33ac5259eeb8a1db241013bc41e9ba5bc2fd74aca12b581b3d7596a",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
                }
            }
        }
    }
]

```

### in this case you can see like this  "IPAddress": "172.17.0.2",



```ruby
althaf@mas:~$ docker ps
CONTAINER ID   IMAGE             COMMAND                  CREATED          STATUS          PORTS                                                 NAMES
3771b5c36e63   jenkins/jenkins   "/usr/bin/tini -- /u…"   53 seconds ago   Up 52 seconds   8080/tcp, 50000/tcp                                   distracted_leavitt
ea31344ecd60   postgres          "docker-entrypoint.s…"   10 days ago      Up 3 days       5432/tcp, 0.0.0.0:5434->5434/tcp, :::5434->5434/tcp   django-k8s-postgres_db-1
935762c361a1   redis             "redis-server --appe…"   4 weeks ago      Up 3 days       6379/tcp, 0.0.0.0:6388->6388/tcp, :::6388->6388/tcp   django-k8s-redis_db-1
althaf@mas:~$ docker inspect 3771b5c36e63
[
    {
        "Id": "3771b5c36e63bc938424676956f121ec116015f74bd9d80d5b894cb95a53949c",
        "Created": "2023-10-20T07:20:26.070019477Z",
        "Path": "/usr/bin/tini",
        "Args": [
            "--",
            "/usr/local/bin/jenkins.sh"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 58339,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2023-10-20T07:20:26.643537373Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:892693e4fe3166280952abf6981fa9fb5b451c3be9ce3c689a7f708a6cf87546",
        "ResolvConfPath": "/var/lib/docker/containers/3771b5c36e63bc938424676956f121ec116015f74bd9d80d5b894cb95a53949c/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/3771b5c36e63bc938424676956f121ec116015f74bd9d80d5b894cb95a53949c/hostname",
        "HostsPath": "/var/lib/docker/containers/3771b5c36e63bc938424676956f121ec116015f74bd9d80d5b894cb95a53949c/hosts",
        "LogPath": "/var/lib/docker/containers/3771b5c36e63bc938424676956f121ec116015f74bd9d80d5b894cb95a53949c/3771b5c36e63bc938424676956f121ec116015f74bd9d80d5b894cb95a53949c-json.log",
        "Name": "/distracted_leavitt",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "docker-default",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "ConsoleSize": [
                24,
                80
            ],
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "private",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": [],
            "BlkioDeviceWriteBps": [],
            "BlkioDeviceReadIOps": [],
            "BlkioDeviceWriteIOps": [],
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": null,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/4fcda6bf46824386019fcf96b364b8364b525b594e4674cb25a1c13be278ca6b-init/diff:/var/lib/docker/overlay2/690c5f789ba9ea4635d908344ebd71653e5dc4ab0efe555ddbb2240472d7d885/diff:/var/lib/docker/overlay2/38ccfbc20dd34bc3833cbcca0dcc64fcbfc6138d0216edcb8b54e9765645fe0b/diff:/var/lib/docker/overlay2/fa5fcc7e93637e275f366d70c1a22cc5d8541d3796af49c6bdb4f55d93b264b0/diff:/var/lib/docker/overlay2/89783e54ac1655ccfa289dc8fe92e9b34412c935df8d2bf165e47afa3f2d4414/diff:/var/lib/docker/overlay2/9d396ec863c4969b4cbaac7780af21a409fa4d613405f4c4b2867e9dc3c0c2ea/diff:/var/lib/docker/overlay2/40c102ac131d8b5630f7bff8ac35d93b562e2ad4f8042ee8595fe72cdb2021ae/diff:/var/lib/docker/overlay2/193c47362c60c5eb0a2d1295eb210629d6b2dc117a3dea954db5a8ba58ae64b3/diff:/var/lib/docker/overlay2/0bdc7769f1a46bb9b434f1627b14468b958753b96e80564c76ad81bd86468ed5/diff:/var/lib/docker/overlay2/2786edd85db6e00cc94f76d6159d6bc284a2dc69d6d3560355a143303ab8ee8c/diff:/var/lib/docker/overlay2/de7600cb077a6501e7965447eecbae1521c7ba3c91e4f459dbd57beffa5c4432/diff:/var/lib/docker/overlay2/f1fe023a904f47f8663e64b18aaba99977c904be41b15922cde8f1b0e97b4de7/diff:/var/lib/docker/overlay2/3d30e1f7ad524bc7612f3dfe84be28b35751b51572c4bebd11aa4289291633b6/diff",
                "MergedDir": "/var/lib/docker/overlay2/4fcda6bf46824386019fcf96b364b8364b525b594e4674cb25a1c13be278ca6b/merged",
                "UpperDir": "/var/lib/docker/overlay2/4fcda6bf46824386019fcf96b364b8364b525b594e4674cb25a1c13be278ca6b/diff",
                "WorkDir": "/var/lib/docker/overlay2/4fcda6bf46824386019fcf96b364b8364b525b594e4674cb25a1c13be278ca6b/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [
            {
                "Type": "volume",
                "Name": "5329ca9fd236909932f5134e77b455190b03f4b9b898d6e5d3520b82dc9f9b7c",
                "Source": "/var/lib/docker/volumes/5329ca9fd236909932f5134e77b455190b03f4b9b898d6e5d3520b82dc9f9b7c/_data",
                "Destination": "/var/jenkins_home",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            }
        ],
        "Config": {
            "Hostname": "3771b5c36e63",
            "Domainname": "",
            "User": "jenkins",
            "AttachStdin": false,
            "AttachStdout": true,
            "AttachStderr": true,
            "ExposedPorts": {
                "50000/tcp": {},
                "8080/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/opt/java/openjdk/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "LANG=C.UTF-8",
                "JENKINS_HOME=/var/jenkins_home",
                "JENKINS_SLAVE_AGENT_PORT=50000",
                "REF=/usr/share/jenkins/ref",
                "JENKINS_VERSION=2.428",
                "JENKINS_UC=https://updates.jenkins.io",
                "JENKINS_UC_EXPERIMENTAL=https://updates.jenkins.io/experimental",
                "JENKINS_INCREMENTALS_REPO_MIRROR=https://repo.jenkins-ci.org/incrementals",
                "COPY_REFERENCE_FILE_LOG=/var/jenkins_home/copy_reference_file.log",
                "JAVA_HOME=/opt/java/openjdk"
            ],
            "Cmd": null,
            "Image": "jenkins/jenkins",
            "Volumes": {
                "/var/jenkins_home": {}
            },
            "WorkingDir": "",
            "Entrypoint": [
                "/usr/bin/tini",
                "--",
                "/usr/local/bin/jenkins.sh"
            ],
            "OnBuild": null,
            "Labels": {
                "org.opencontainers.image.description": "The Jenkins Continuous Integration and Delivery server",
                "org.opencontainers.image.licenses": "MIT",
                "org.opencontainers.image.revision": "115be7ff772fd576113d3db80c14c82ec28587fb",
                "org.opencontainers.image.source": "https://github.com/jenkinsci/docker",
                "org.opencontainers.image.title": "Official Jenkins Docker image",
                "org.opencontainers.image.url": "https://www.jenkins.io/",
                "org.opencontainers.image.vendor": "Jenkins project",
                "org.opencontainers.image.version": "2.428"
            }
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "07684fae1d9f04a71ca06c953a711919610aff81f3af720d947da1b46b7386a3",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {
                "50000/tcp": null,
                "8080/tcp": null
            },
            "SandboxKey": "/var/run/docker/netns/07684fae1d9f",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "f7f26e59f33ac5259eeb8a1db241013bc41e9ba5bc2fd74aca12b581b3d7596a",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            -"IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "9139b1e3e9c2094b900f3dec66bf7a91e315529316ef82c732eeb7cd919eb51b",
                    "EndpointID": "f7f26e59f33ac5259eeb8a1db241013bc41e9ba5bc2fd74aca12b581b3d7596a",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
                }
            }
        }
    }
]
althaf@mas:~$

```
### try to log in through internal ip


![Screenshot from 2023-10-20 11-45-13](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/9153d275-8a17-49d0-9051-2dcecfd7e872)

![Screenshot from 2023-10-20 11-51-29](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/7b502e35-8c04-483a-8e00-8d1d7ee1d1a9)

### login through the password generated by when we run the jenkins on docker


![Screenshot from 2023-10-20 11-46-14](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/b5f1bb48-eb3e-49fc-ac36-a1860cf4f15f)

![Screenshot from 2023-10-20 11-49-24](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/c309493d-e013-4f18-b1b9-653e572eab4b)



# log in through port maping 
***makesure the container is stopped***
```ruby
docker run -p 8080:8080 jenkins/jenkins
```


```ruby
althaf@mas:~$ docker run -p 8080:8080 jenkins/jenkins
Running from: /usr/share/jenkins/jenkins.war
webroot: /var/jenkins_home/war
2023-10-20 07:56:00.349+0000 [id=1]	INFO	winstone.Logger#logInternal: Beginning extraction from war file
2023-10-20 07:56:00.904+0000 [id=1]	WARNING	o.e.j.s.handler.ContextHandler#setContextPath: Empty contextPath
2023-10-20 07:56:00.960+0000 [id=1]	INFO	org.eclipse.jetty.server.Server#doStart: jetty-10.0.17; built: 2023-10-02T04:04:10.314Z; git: a0f5f05abaa6c3aabb7c3d35f10a6f412ab8b05f; jvm 17.0.8.1+1
2023-10-20 07:56:01.155+0000 [id=1]	INFO	o.e.j.w.StandardDescriptorProcessor#visitServlet: NO JSP Support for /, did not find org.eclipse.jetty.jsp.JettyJspServlet
2023-10-20 07:56:01.195+0000 [id=1]	INFO	o.e.j.s.s.DefaultSessionIdManager#doStart: Session workerName=node0
2023-10-20 07:56:01.636+0000 [id=1]	INFO	hudson.WebAppMain#contextInitialized: Jenkins home directory: /var/jenkins_home found at: EnvVars.masterEnvVars.get("JENKINS_HOME")
2023-10-20 07:56:01.737+0000 [id=1]	INFO	o.e.j.s.handler.ContextHandler#doStart: Started w.@4d8286c4{Jenkins v2.428,/,file:///var/jenkins_home/war/,AVAILABLE}{/var/jenkins_home/war}
2023-10-20 07:56:01.748+0000 [id=1]	INFO	o.e.j.server.AbstractConnector#doStart: Started ServerConnector@37ddb69a{HTTP/1.1, (http/1.1)}{0.0.0.0:8080}
2023-10-20 07:56:01.758+0000 [id=1]	INFO	org.eclipse.jetty.server.Server#doStart: Started Server@43aaf813{STARTING}[10.0.17,sto=0] @1830ms
2023-10-20 07:56:01.759+0000 [id=27]	INFO	winstone.Logger#logInternal: Winstone Servlet Engine running: controlPort=disabled
2023-10-20 07:56:01.936+0000 [id=35]	INFO	jenkins.InitReactorRunner$1#onAttained: Started initialization
2023-10-20 07:56:01.948+0000 [id=46]	INFO	jenkins.InitReactorRunner$1#onAttained: Listed all plugins
2023-10-20 07:56:02.596+0000 [id=45]	INFO	jenkins.InitReactorRunner$1#onAttained: Prepared all plugins
2023-10-20 07:56:02.600+0000 [id=45]	INFO	jenkins.InitReactorRunner$1#onAttained: Started all plugins
2023-10-20 07:56:02.605+0000 [id=45]	INFO	jenkins.InitReactorRunner$1#onAttained: Augmented all extensions
2023-10-20 07:56:02.747+0000 [id=45]	INFO	jenkins.InitReactorRunner$1#onAttained: System config loaded
2023-10-20 07:56:02.748+0000 [id=45]	INFO	jenkins.InitReactorRunner$1#onAttained: System config adapted
2023-10-20 07:56:02.748+0000 [id=47]	INFO	jenkins.InitReactorRunner$1#onAttained: Loaded all jobs
2023-10-20 07:56:02.750+0000 [id=46]	INFO	jenkins.InitReactorRunner$1#onAttained: Configuration for all jobs updated
2023-10-20 07:56:02.776+0000 [id=61]	INFO	hudson.util.Retrier#start: Attempt #1 to do the action check updates server
2023-10-20 07:56:03.040+0000 [id=35]	INFO	jenkins.install.SetupWizard#init:

```
# use this password for login

```ruby
*************************************************************
*************************************************************
*************************************************************

Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

3856e16dc2ec48b6852d1dc5924a229c

This may also be found at: /var/jenkins_home/secrets/initialAdminPassword

*************************************************************
*************************************************************
*************************************************************

2023-10-20 07:56:24.683+0000 [id=61]	INFO	h.m.DownloadService$Downloadable#load: Obtained the updated data file for hudson.tasks.Maven.MavenInstaller
2023-10-20 07:56:24.684+0000 [id=61]	INFO	hudson.util.Retrier#start: Performed the action check updates server successfully at the attempt #1
2023-10-20 07:56:25.194+0000 [id=35]	INFO	jenkins.InitReactorRunner$1#onAttained: Completed initialization
2023-10-20 07:56:25.209+0000 [id=26]	INFO	hudson.lifecycle.Lifecycle#onReady: Jenkins is fully up and running

```
![Screenshot from 2023-10-20 11-58-44](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/2ee609b7-4512-4e1e-8670-f582448cf6a7)

```ruby
althaf@mas:~$ docker exec f7e12068655c cat /var/jenkins_home/secrets/initialAdminPassword
3856e16dc2ec48b6852d1dc5924a229c

```
![Screenshot from 2023-10-20 12-10-51](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/440ca1d2-d664-4d1c-aa4c-47da160e9dd6)

# so now i want this data should be persisted other wise everytime i use the jenkins i have to set form the beggineng stage

### Created folder locally to store my data
```ruby
althaf@mas:~$ mkdir my-jenkins-data
```
```ruby
docker run -p 8080:8080 -v /home/althaf/my-jenkins-data:/var/jenkins_home -u root jenkins/jenkins
```

```ruby
althaf@mas:~$ docker run -p 8080:8080 -v /home/althaf/my-jenkins-data:/var/jenkins_home -u root jenkins/jenkins
Running from: /usr/share/jenkins/jenkins.war
webroot: /var/jenkins_home/war
2023-10-20 08:22:25.403+0000 [id=1]	INFO	winstone.Logger#logInternal: Beginning extraction from war file

```
The command you provided is a Docker command used to run a Docker container using the official Jenkins Docker image. Let's break down the command step by step:

1. `docker run`: This is the command to run a Docker container.

2. `-p 8080:8080`: This is an option to map a port from the host machine to the container. It tells Docker to forward traffic from port 8080 on your host machine to port 8080 inside the container. In the context of Jenkins, this means that you can access the Jenkins web interface on your host machine by visiting http://localhost:8080.

3. `-v /home/althaf/my-jenkins-data:/var/jenkins_home`: This is an option to create a volume. It tells Docker to create a named volume that maps the directory `/home/althaf/my-jenkins-data` on your host machine to the directory `/var/jenkins_home` inside the container. This is commonly used to persist data and configurations across container restarts. In this case, it's used to store Jenkins data and settings.

4. `-u root`: This is an option to specify the user to run the container as. It sets the user to "root" inside the container. Running the container as root can be necessary for certain operations that require elevated privileges.

5. `jenkins/jenkins`: This is the name of the Docker image to run. In this case, it's the official Jenkins Docker image, specifically the "jenkins/jenkins" image. Docker will pull this image from Docker Hub if it's not already downloaded on your system.

So, in summary, this Docker command runs a Jenkins container, exposing its web interface on port 8080 of the host machine, using a volume to persist Jenkins data and settings in the `/home/althaf/my-jenkins-data` directory on the host, and running the container as the root user. This is a common setup for running Jenkins in a Docker container, allowing you to maintain your Jenkins configuration and data even if the container is stopped or removed.

# created a Test job in jenkins. makesure the data is persisted 
![Screenshot from 2023-10-20 12-44-30](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/0254d2c7-ad93-4464-a47e-1707857ec602)



# Stopped the docker container 
```ruby
althaf@mas:~$ docker ps
CONTAINER ID   IMAGE             COMMAND                  CREATED          STATUS          PORTS                                                  NAMES
87a9689ab962   jenkins/jenkins   "/usr/bin/tini -- /u…"   14 minutes ago   Up 14 minutes   0.0.0.0:8080->8080/tcp, :::8080->8080/tcp, 50000/tcp   elegant_rubin
ea31344ecd60   postgres          "docker-entrypoint.s…"   10 days ago      Up 3 days       5432/tcp, 0.0.0.0:5434->5434/tcp, :::5434->5434/tcp    django-k8s-postgres_db-1
935762c361a1   redis             "redis-server --appe…"   4 weeks ago      Up 3 days       6379/tcp, 0.0.0.0:6388->6388/tcp, :::6388->6388/tcp    django-k8s-redis_db-1


althaf@mas:~$ docker stop 87a9689ab962
87a9689ab962
```


![Screenshot from 2023-10-20 12-46-39](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/b6cd341d-b5d1-461c-8890-52fe167ad659)

![Screenshot from 2023-10-20 12-46-05](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/8e53ff7a-bcaf-4b11-b4f6-83af5bf4feac)



# Again start the Container this time the data is persisted

![Screenshot from 2023-10-20 12-38-36](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/a6938d0b-91d6-4c66-85b7-514f0bd23281)
![Screenshot from 2023-10-20 12-39-05](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/436f4d7f-b512-499e-97fa-b68a5d3ada76)





