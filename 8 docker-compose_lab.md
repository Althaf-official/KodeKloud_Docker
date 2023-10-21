# First create a redis database container called redis, image redis:alpine.

```ruby
docker run --name redis -d redis:alpine
```
The command `docker run --name redis -d redis:alpine` is used to start a Docker container running the Redis database server using the official Redis Docker image tagged as "alpine." Let's break down this command step by step:

1. `docker run`: This is the command to create and start a Docker container.

2. `--name redis`: This part of the command specifies the name you want to give to the container. In this case, the container is named "redis." Naming containers can be useful for easy identification and management of containers.

3. `-d`: This is a flag that stands for "detached." It tells Docker to run the container in the background, allowing you to continue using your terminal for other commands while the container runs in the background.

4. `redis:alpine`: This is the argument that specifies the Docker image you want to use for creating the container. In this case, it refers to the official Redis Docker image tagged as "alpine." The "alpine" tag indicates that this image is based on the Alpine Linux distribution, which is known for its lightweight and minimalistic nature.

So, when you run this command, Docker will create a new container based on the Redis image, give it the name "redis," and start it in the background. The Redis container will be running as a detached process, and you can use it for applications that require a Redis database server.

This command is a basic example of how to start a Docker container. It sets a name for the container, runs it in the background, and specifies the image to use. The actual usage of the Redis server within the container depends on your application needs.

# Next, create a simple container called clickcounter with the image kodekloud/click-counter, link it to the redis container that we created in the previous task and then expose it on the host port 8085


The clickcounter app run on port 5000.
if you are unsure, check the hints section for the exact commands.


clickcounter exposed on the correct HostPort?

clickcounter linked to the redis container ?

Run the command:
```ruby
docker run -d --name=clickcounter --link redis:redis -p 8085:5000 kodekloud/click-counter
```

# Create a docker-compose.yml file under the directory /root/clickcounter. Once done, run docker-compose up.


The compose file should have the exact specification as follows -

redis service specification - Image name should be redis:alpine.
clickcounter service specification - Image name should be kodekloud/click-counter, app is run on port 5000 and expose it on the host port 8085 in the compose file.


syntax check for the docker-compose.yml

clickcounter running on the correct HostPort?

clickcounter webpage working correctly?

Use the below compose file:

```ruby

services:
  redis:
    image: redis:alpine
  clickcounter:
    image: kodekloud/click-counter
    ports:
    - 8085:5000
version: '3.0'

```
Then run a docker-compose up -d command.
To run containers in a background, added -d flag.
