# Inspect the environment variables set on the running container and identify the value set to the APP_COLOR variable.
```ruby
       },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "APP_COLOR=pink",
                "PATH=/usr/local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "LANG=C.UTF-8",
                "GPG_KEY=0D96DF4D4110E5C43FBFB17F2D347EA6AA65421D",
                "PYTHON_VERSION=3.6.6",
                "PYTHON_PIP_VERSION=18.1"
            ],
            "Cmd": null,
            "Image": "kodekloud/simple-webapp",
            "Volumes": null,
            "WorkingDir": "/opt",
            "Entrypoint": [
                "python",
                "app.py"
            ],
            "OnBuild": null,
            "Labels": {}
        },
```

# Run a container named blue-app using image kodekloud/simple-webapp and set the environment variable APP_COLOR to blue. Make the application available on port 38282 on the host. The application listens on port 8080.


Name: blue-app

Image: kodekloud/simple-webapp

ENV Variable: APP_COLOR=blue

```ruby
$ docker run -p 38282:8080 --name blue-app -e APP_COLOR=blue -d kodekloud/simple-webapp
24e36bf22bfc908cd3c9f1eeba6fa8b3d4cb3154529de87de2e622033eaba815
```

### To know the env field from within a webapp container, run docker exec -it blue-app env
```ruby
$ docker exec -it blue-app env
PATH=/usr/local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOSTNAME=24e36bf22bfc
TERM=xterm
APP_COLOR=blue
LANG=C.UTF-8
GPG_KEY=0D96DF4D4110E5C43FBFB17F2D347EA6AA65421D
PYTHON_VERSION=3.6.6
PYTHON_PIP_VERSION=18.1
HOME=/root
$ 
```
# Deploy a mysql database using the mysql image and name it mysql-db.

Set the database password to use db_pass123. Lookup the mysql image on Docker Hub and identify the correct environment variable to use for setting the root password.

Name: mysql-db

Image: mysql

Env: MYSQL_ROOT_PASSWORD=db_pass123

```ruby
HINT: Run the command: docker run -d -e MYSQL_ROOT_PASSWORD=db_pass123 --name mysql-db mysql

To know the env field from within a mysql-db container, run docker exec -it mysql-db env



$ docker run -d -e MYSQL_ROOT_PASSWORD=db_pass123 --name mysql-db mysql
d957b9829466144704a7e0cba4fc3f2cf0ed9b422e4d1e761c991ca9c8a5c193



$ docker exec -it mysql-db env
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOSTNAME=d957b9829466
TERM=xterm
MYSQL_ROOT_PASSWORD=db_pass123
GOSU_VERSION=1.16
MYSQL_MAJOR=8.0
MYSQL_VERSION=8.0.33-1.el8
MYSQL_SHELL_VERSION=8.0.33-1.el8
HOME=/root
$ 


```

