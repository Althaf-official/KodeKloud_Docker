
```ruby
althaf@mas:~/dev/Docker/Voting-App$ pwd
/home/althaf/dev/Docker/Voting-App


althaf@mas:~/dev/Docker/Voting-App$ git clone https://github.com/dockersamples/example-voting-app.git




althaf@mas:~/dev/Docker/Voting-App$ ls
example-voting-app

althaf@mas:~/dev/Docker/Voting-App$ cd example-voting-app/
althaf@mas:~/dev/Docker/Voting-App/example-voting-app$ ls
architecture.excalidraw.png  docker-compose.yml  healthchecks        LICENSE      README.md  seed-data  worker
docker-compose.images.yml    docker-stack.yml    k8s-specifications  MAINTAINERS  result     vote


althaf@mas:~/dev/Docker/Voting-App/example-voting-app$ ls -al
total 224
drwxrwxr-x  4 althaf althaf   4096 Oct 21 16:45 result
drwxrwxr-x  2 althaf althaf   4096 Oct 21 16:45 seed-data
drwxrwxr-x  4 althaf althaf   4096 Oct 21 16:45 vote
drwxrwxr-x  2 althaf althaf   4096 Oct 21 16:45 worker



althaf@mas:~/dev/Docker/Voting-App/example-voting-app$ cd vote/
althaf@mas:~/dev/Docker/Voting-App/example-voting-app/vote$ ls
app.py  Dockerfile  requirements.txt  static  templates



althaf@mas:~/dev/Docker/Voting-App/example-voting-app/vote$ cat Dockerfile 
# Using official python runtime base image
FROM python:3.9-slim

# add curl for healthcheck
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Set the application directory
WORKDIR /app

# Install our requirements.txt
COPY requirements.txt /app/requirements.txt
RUN pip install -r requirements.txt

# Copy our code from the current folder to /app inside the container
COPY . .

# Make port 80 available for links and/or publish
EXPOSE 80

# Define our command to be run when launching the container
CMD ["gunicorn", "app:app", "-b", "0.0.0.0:80", "--log-file", "-", "--access-logfile", "-", "--workers", "4", "--keep-alive", "0"]






althaf@mas:~/dev/Docker/Voting-App/example-voting-app/vote$ docker build . -t voting-app
[+] Building 20.0s (12/12) FINISHED                                  docker:default



althaf@mas:~/dev/Docker/Voting-App/example-voting-app/vote$ ls                      
app.py  Dockerfile  requirements.txt  static  templates





althaf@mas:~/dev/Docker/Voting-App/example-voting-app/vote$ docker images
REPOSITORY                                                              TAG       IMAGE ID       CREATED          SIZE
voting-app                                                              latest    d8675acd6b1a   29 seconds ago   145MB
                                                             latest    f7d9a0d4223b   5 weeks ago      417MB


althaf@mas:~/dev/Docker/Voting-App/example-voting-app/vote$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
````


```ruby
docker run -p 5000:80 voting-app
```


```ruby
althaf@mas:~/dev/Docker/Voting-App/example-voting-app/vote$ docker run -p 5000:80 voting-app
[2023-10-21 12:51:58 +0000] [1] [INFO] Starting gunicorn 21.2.0
[2023-10-21 12:51:58 +0000] [1] [INFO] Listening at: http://0.0.0.0:80 (1)
1; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/117.0.0.0 Safari/537.36"

```
# 3 Check the Ip address that the container listening

```ruby
althaf@mas:~/dev/Docker/Voting-App/example-voting-app/vote$ docker ps
CONTAINER ID   IMAGE        COMMAND                  CREATED              STATUS          PORTS                                   NAMES
9cd5b7ab6261   voting-app   "gunicorn app:app -b…"   About a minute ago   Up 59 seconds   0.0.0.0:5000->80/tcp, :::5000->80/tcp   stupefied_carver

# inspect

althaf@mas:~/dev/Docker/Voting-App/example-voting-app/vote$ docker inspect 9cd5b7ab6261
[
    {
        "Id": "9cd5b7ab6261e329fdc69272d23f564c37f97f96e6ae41050af2d128f07d68c6",
        "Created": "2023-10-21T12:51:58.267533537Z",
        "Path": "gunicorn",
      
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "9139b1e3e9c2094b900f3dec66bf7a91e315529316ef82c732eeb7cd919eb51b",
                    "EndpointID": "61ffaaf315c54c355369a83e893572d1c5b5009a4b18dcd2308c320c7fd382c4",
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
althaf@mas:~/dev/Docker/Voting-App/example-voting-app/vote$ 
```
![Screenshot from 2023-10-21 17-08-59](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/042db148-8659-45c0-a399-121e05d0b330)

# when we click the Dog or cat the docker container is showing error that redis not configured

# SO RUN REDIS CONTAINER 

```ruby
docker run --name=redis redis
```
### --name=redis: This part of the command specifies the name you want to give to the container. In this case, the container is named "redis." 
### Naming containers can be useful for easy identification and management of containers.

```
Here's what happens in summary:

docker run: Start a new Docker container.
--name=redis: Name the container "redis."
redis: Use the Redis Docker image to create the container.
```

# then run the voting app
```ruby
docker run -p 5000:80 --link redis:redis voting-app
```

### `--link redis:redis`: This part establishes a network link between the current container (in this case, the "voting-app" container) and another container named "redis." 

### The format is "--link [container_name]:[alias]." This allows the "voting-app" container to communicate with the "redis" container using the alias "redis" as the hostname.

![Screenshot from 2023-10-21 17-36-56](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/4f8fe2af-58bd-4788-9c8e-841e5bef973d)

NOW SUCCESFULLY CAN CLICK DOG OR CAT




# NOW WE WILL PROCEED TO THE WORKER
![Screenshot from 2023-10-21 17-39-58](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/6bf2f15c-2537-4f30-9923-e74df8917e9d)

### FOR THE WORKER PREREQISETS IS THE POSTGRESS DATABASE


### so we run the postgress database .makesure the postgress version on docker_compose.yaml

```ruby
docker run --name=db -e POSTGRES_PASSWORD=postgres postgres:15-alpine
```
![Screenshot from 2023-10-21 18-53-47](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/aa1a10b8-034a-4c85-8973-c7a9ed011480)


```
So, when you run this command, Docker will create a new container based on the PostgreSQL image, set the container's name to "db," and configure the PostgreSQL superuser password to "your_password" using the POSTGRES_PASSWORD environment variable. The PostgreSQL container will be up and running, ready to be used.
Here's a summary of the command:
docker run: Start a new Docker container.
--name=db: Name the container "db."
-e POSTGRES_PASSWORD=your_password: Set the PostgreSQL superuser password using an environment variable.
postgres:15-alpine: Use the PostgreSQL Docker image with version 15 based on Alpine Linux.
```
![Screenshot from 2023-10-21 18-24-36](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/75d2f7dc-9f19-4c8a-a662-7455977eec45)
now i have 3 container is runnig

### now i have to build the worker-app image

cd /worker

```ruby
docker build . -t worker-app
```
![Screenshot from 2023-10-21 18-35-33](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/8ff0be4d-b667-4cc7-a19c-0587521272e3)

### now i've 4 images
```ruby
althaf@mas:~/dev/Docker/Voting-App/example-voting-app/worker$ docker images
REPOSITORY                                                              TAG         IMAGE ID       CREATED         SIZE
worker-app                                                              latest      2ccc616e9570   3 minutes ago   194MB
voting-app                                                              latest      d8675acd6b1a   2 hours ago     145MB
redis                                                                   latest      e579380d4317   3 days ago      138MB
postgres                                                                15-alpine   d43df62c9cb9   2 weeks ago     237MB
althaf@mas:~/dev/Docker/Voting-App/example-voting-app/worker$ 

```
# run the worker-app

```ruby
althaf@mas:~/dev/Docker/Voting-App/example-voting-app/worker$ docker run --link redis:redis --link db:db -e POSTGRES_PASSWORD=postgres worker-app
Connected to db
Connecting to redis
Found redis at 172.17.0.2
```
# Build result-app image 
```ruby

althaf@mas:~/dev/Docker/Voting-App/example-voting-app$ cd result/
althaf@mas:~/dev/Docker/Voting-App/example-voting-app/result$ ls
docker-compose.test.yml  Dockerfile  package.json  package-lock.json  server.js  tests  views



althaf@mas:~/dev/Docker/Voting-App/example-voting-app/result$ cat Dockerfile 
FROM node:18-slim

# add curl for healthcheck
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    curl \
    tini \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# have nodemon available for local dev use (file watching)
RUN npm install -g nodemon

COPY package*.json ./

RUN npm ci \
 && npm cache clean --force \
 && mv /app/node_modules /node_modules

COPY . .

ENV PORT 80
EXPOSE 80

ENTRYPOINT ["/usr/bin/tini", "--"]
CMD ["node", "server.js"]
```
```ruby
docker build . -t result-app
```

```ruby
althaf@mas:~/dev/Docker/Voting-App/example-voting-app/result$ docker build . -t result-app
[+] Building 39.3s (13/13) FINISHED                                                                   docker:default
 => [internal] load .dockerignore                                                                               0.0s
 => => transferring context: 54B                                                                                0.0s
 => [internal] load build definition from Dockerfile                                                            0.0s

```
then inspect the ip of result app

![Screenshot from 2023-10-21 19-13-41](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/22b1727e-976b-459c-a3f6-1e339b6b31f6)
![Screenshot from 2023-10-21 19-12-46](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/7bee4199-26dd-4012-ac52-a4266a3a9457)
![Screenshot from 2023-10-21 19-16-57](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/ff3daef7-e8ea-48d2-980e-d9b3f9dc3d13)
![Screenshot from 2023-10-21 19-17-02](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/15b67760-6782-4dc7-a974-0672e08048e3)
