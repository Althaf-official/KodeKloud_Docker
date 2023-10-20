### Let us first inspect the environment. How many containers are running on this host?

```ruby
        Welcome to the KodeKloud Hands-On lab                                                                                          
    __ ______  ____  ________ __ __    ____  __  ______ 
   / //_/ __ \/ __ \/ ____/ //_// /   / __ \/ / / / __ \
  / ,< / / / / / / / __/ / ,<  / /   / / / / / / / / / /
 / /| / /_/ / /_/ / /___/ /| |/ /___/ /_/ / /_/ / /_/ / 
/_/ |_\____/_____/_____/_/ |_/_____/\____/\____/_____/  
                                                        
              All rights reserved                                                                                                       
$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                                           NAMES
d1c9c68a3761   nginx:alpine   "/docker-entrypoint.…"   43 seconds ago   Up 41 seconds   0.0.0.0:3456->3456/tcp, 0.0.0.0:38080->80/tcp   distracted_taussig
$ 
```

### How many ports are published on this container?
Run the command docker ps and look under the `PORTS` column.
```ruby
0.0.0.0:3456->3456/tcp, 0.0.0.0:38080->80/tcp 
```

### Which of the below ports are the exposed on the CONTAINER?

0.0.0.0:3456->`3456`/tcp, 0.0.0.0:38080->`80`/tcp

```3456 & 80```

### Which of the below ports are published on Host?

Run the command docker ps and look under the PORTS column. Ports on the left(before ->) are published on the host.

```ruby
0.0.0.0:3456->`3456`/tcp, 0.0.0.0:38080->`80`/tcp
```

``` 38080 & 3456 ```

### Run an instance of kodekloud/simple-webapp with a tag blue and map port 8080 on the container to 38282 on the host.



Image: kodekloud/simple-webapp:blue

Container Port: 8080

Host Port: 38282

```ruby
docker run -p 38282:8080 kodekloud/simple-webapp:blue
```
To run an instance of the `kodekloud/simple-webapp` Docker image with the tag `blue` and map port 8080 on the container to port 38282 on the host, you can use the `docker run` command. Here's the command:

```bash
docker run -p 38282:8080 kodekloud/simple-webapp:blue
```

Let's break down the command:

- `docker run`: This is the command to run a Docker container.

- `-p 38282:8080`: This option maps port 38282 on the host to port 8080 on the container. It specifies that incoming traffic to port 38282 on the host should be forwarded to port 8080 inside the container.

- `kodekloud/simple-webapp:blue`: This specifies the Docker image to run. It uses the `kodekloud/simple-webapp` image with the `blue` tag.

Running this command will start an instance of the `kodekloud/simple-webapp` Docker image with the `blue` tag, and you can access the web application hosted inside the container by visiting http://localhost:38282 in your web browser.


```ruby
$ docker run -p 38282:8080 kodekloud/simple-webapp:blue
Unable to find image 'kodekloud/simple-webapp:blue' locally
blue: Pulling from kodekloud/simple-webapp
4fe2ade4980c: Already exists 
7cf6a1d62200: Already exists 
f0d690b9e495: Already exists 
fac5d45ad062: Already exists 
a6fc8a0deb7d: Pull complete 
f43c8e496f88: Pull complete 
58ca939f7651: Pull complete 
095a1a007cdb: Pull complete 
Digest: sha256:9caf15476dc60b77c7460791bea8ea5f6ca02b90199aabe088beea83bc943fe5
Status: Downloaded newer image for kodekloud/simple-webapp:blue
 * Serving Flask app "app" (lazy loading)
 * Environment: production
   WARNING: Do not use the development server in a production environment.
   Use a production WSGI server instead.
 * Debug mode: off
 * Running on http://0.0.0.0:8080/ (Press CTRL+C to quit)
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

