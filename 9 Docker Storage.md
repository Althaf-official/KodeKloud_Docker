# What location are the files related to the docker containers and images stored?

/var/lib/docker

# What directory under /var/lib/docker are the files related to the container alpine-3 image stored?

The directory name is the same as the container id.

It's available in the location /var/lib/docker/containers/.

Run `docker ps -a` command and match the container id of alpine-3 with the directory name.

# Run a mysql container named mysql-db using the mysql image. Set database password to db_pass123

```ruby
docker run -d --name mysql-db -e MYSQL_ROOT_PASSWORD=db_pass123 mysql
```

# Run a mysql container again, but this time map a volume to the container so that the data stored by the container is stored at /opt/data on the host.


Use the same name : mysql-db and same password: db_pass123 as before. Mysql stores data at /var/lib/mysql inside the container.



Correct Password set

Host: /opt/data

Container: /var/lib/mysql

```ruby
docker run -v /opt/data:/var/lib/mysql -d --name mysql-db -e MYSQL_ROOT_PASSWORD=db_pass123 mysql
```

The command `docker run -v /opt/data:/var/lib/mysql -d --name mysql-db -e MYSQL_ROOT_PASSWORD=db_pass123 mysql` is used to start a Docker container running a MySQL database server. The `-v` flag in the command is used to create a volume (data storage) for the MySQL container. Let's break down the part of the command that specifies the volume:

- `-v /opt/data:/var/lib/mysql`: This part of the command is used to create a volume and map it to a specific directory within the container. The format for the `-v` flag is `/host/directory:/container/directory`.

   - `/opt/data`: This is the path to a directory on the host machine. In this case, it's the directory `/opt/data`. This is where you want to store your MySQL data on the host.

   - `/var/lib/mysql`: This is the path to the directory within the MySQL container where MySQL stores its data by default. By mapping the host directory to this container directory, you are effectively telling Docker to use the host directory (`/opt/data`) to store the MySQL data.

By using this volume mapping, you achieve a couple of important benefits:

1. **Data Persistence**: Any data written to the `/var/lib/mysql` directory inside the container (where MySQL stores its data) will be stored on the host machine in the `/opt/data` directory. This means that even if the MySQL container is stopped or removed, the data will persist on the host machine. It's a way to make sure that your database data survives container restarts and updates.

2. **Data Sharing**: It allows you to share data between the host and the container. Data written to `/var/lib/mysql` in the container will be reflected in `/opt/data` on the host, and vice versa. This can be helpful for backup, data import/export, or sharing data between containers.

So, in summary, the `-v /opt/data:/var/lib/mysql` part of the command sets up a volume mapping that links the `/opt/data` directory on the host to the `/var/lib/mysql` directory in the MySQL container. This enables data persistence and sharing between the host and the container, making it useful for managing the MySQL data in a Dockerized environment.


# Disaster strikes.. again! And the database crashed again. But this time we have the data stored at /opt/data directory. Re-deploy a new mysql instance using the same options as before.


Just run the same command as before. Here it is for your convenience: `docker run -v /opt/data:/var/lib/mysql -d --name mysql-db -e MYSQL_ROOT_PASSWORD=db_pass123 mysql`



