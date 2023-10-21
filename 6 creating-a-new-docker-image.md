# Creating a Docker Image


```ruby
docker run -it ubuntu bash
```

```ruby
althaf@mas:~$ docker run -it ubuntu bash
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
aece8493d397: Pull complete 
Digest: sha256:2b7412e6465c3c7fc5bb21d3e6f1917c167358449fecac8176c6e496e5c1f05f
Status: Downloaded newer image for ubuntu:latest
root@e1465bb5f052:/# 

```

The command "docker run -it ubuntu bash" is used to run a Docker container based on the official Ubuntu image and open an interactive Bash shell session within that container. Let's break down the command:

1. **docker run**: This part of the command is used to run a Docker container. Docker is a platform for developing, shipping, and running applications in containers. The "docker run" command is used to start a new container from an image.

2. **-it**: These are two options or flags that are often used together:
   - `-i` (or `--interactive`): It allows you to keep STDIN open and interact with the container.
   - `-t` (or `--tty`): It allocates a pseudo-TTY (terminal) for the container.

   When you use both `-i` and `-t`, you are essentially telling Docker to run the container in an interactive mode with a terminal.

3. **ubuntu**: This is the name of the Docker image from which the container is created. In this case, it's the official Ubuntu image available on the Docker Hub. Docker images are pre-configured, read-only filesystems that serve as the basis for containers.

4. **bash**: This is the command that you want to run inside the container. In this case, you are starting an interactive Bash shell within the container. Once the container is running, you'll be able to execute Bash commands and interact with the Ubuntu environment.

So, when you execute "docker run -it ubuntu bash," Docker will download the Ubuntu image if it's not already present on your system, create a new container from that image, and start an interactive Bash shell session within the container. This is often used for debugging, running commands within a specific environment, or testing software in an isolated environment. When you exit the Bash shell, the container will also stop unless you specify otherwise with the `-d` option to run it in detached mode.

# 1. Install all required dependencies

```ruby
apt-get update
```

```ruby
root@e1465bb5f052:/# apt-get update
Get:1 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Get:17 http://archive.ubuntu.com/ubuntu jammy-backports/universe amd64 Packages [32.6 kB]
Get:18 http://archive.ubuntu.com/ubuntu jammy-backports/main amd64 Packages [78.3 kB]
Fetched 28.0 MB in 10s (2883 kB/s)                                                 
Reading package lists... Done
root@e1465bb5f052:/# 

```

```ruby
apt-get install -y python3
```


```ruby
root@e1465bb5f052:/# apt-get install -y python3
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done

INSTALLING....

Setting up python3 (3.10.6-1~22.04) ...
running python rtupdate hooks for python3.10...
running python post-rtupdate hooks for python3.10...
Processing triggers for libc-bin (2.35-0ubuntu3.4) ...
root@e1465bb5f052:/# 

```
```ruby
python3
```

```ruby
root@e1465bb5f052:/# python3
Python 3.10.12 (main, Jun 11 2023, 05:26:28) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
Type "help", "copyright", "credits" or "license" for more information.
>>> exit()
root@e1465bb5f052:/# 

```

```ruby
apt-get install python3-pip
```

```ruby
root@e1465bb5f052:/# apt-get install python3-pip
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
INSTSALLING python3-pip.....
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.
root@e1465bb5f052:/# 

```
# 2. Install and Configure Web Server

```ruby
pip install flask
```

```ruby
root@e1465bb5f052:/# pip install flask
Collecting flask
  Downloading flask-3.0.0-py3-none-any.whl (99 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 99.7/99.7 KB 2.1 MB/s eta 0:00:00
  Downloading MarkupSafe-2.1.3-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (25 kB)
Installing collected packages: MarkupSafe, itsdangerous, click, blinker, Werkzeug, Jinja2, flask
Successfully installed Jinja2-3.1.2 MarkupSafe-2.1.3 Werkzeug-3.0.0 blinker-1.6.3 click-8.1.7 flask-3.0.0 itsdangerous-2.1.2
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv
root@e1465bb5f052:/# 

```

```ruby
cat > /opt/app.py
```

The command "cat > /opt/app.py" is used in Unix-like operating systems to create or edit a text file named "app.py" in the "/opt" directory. Here's a breakdown of what each part of the command does:

1. `cat`: "cat" is a command-line utility in Unix-like operating systems that is primarily used to concatenate and display the contents of text files. It can also be used to create new files or edit existing ones when combined with input redirection.

2. `>`: This is the output redirection operator. When used in a command, it redirects the output of the command on the left (in this case, "cat") to the file specified on the right (in this case, "/opt/app.py").

3. `/opt/app.py`: This is the file path where you want to create or edit the file. In this case, you're specifying the "/opt" directory, which is typically used for installing optional software or storing application files, and you want to create or edit a file named "app.py" within that directory.

When you run the "cat > /opt/app.py" command, it will effectively open a new file named "app.py" in the "/opt" directory, and any text you type will be written to that file. To save the contents, you typically press Ctrl+D (EOF or end of file) to exit the text input mode and save the file.

Here's a simple example of how to use the "cat >" command to create or edit a file:

1. Open a terminal.
2. Run the command: `cat > /opt/app.py`
3. Type or paste the content you want to be in the "app.py" file.
4. Press Ctrl+D to save and exit.

The file "app.py" will now contain the text you entered. You can use any text editor or viewer to access and edit the contents of this file in the future.

```ruby
root@e1465bb5f052:/# cat > /opt/app.py
import os        
from flask import Flask
app = Flask(__name__)

@app.route("/")
def main():
    return "Welcome!"

@app.route('/how are you')
def hello():
    return 'I am good, how about you?'

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=8080)root@e1465bb5f052:/# 
root@e1465bb5f052:/# 
```

# 3. Start Web Server

```ruby
cd opt/
/opt# FLASK_APP=app.py flask run --host=0.0.0.0
```

```ruby
root@e1465bb5f052:/# cd opt/
root@e1465bb5f052:/opt# FLASK_APP=app.py flask run --host=0.0.0.0
 * Serving Flask app 'app.py'
 * Debug mode: off
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:5000
 * Running on http://172.17.0.2:5000
Press CTRL+C to quit

```
![Screenshot from 2023-10-20 15-43-37](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/878e00b0-1231-44a4-87a1-d4b63275f7a2)
![Screenshot from 2023-10-20 15-43-57](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/0743bd16-e0e5-4383-a0ec-20dc49a04a0e)

# now my flask app is running
# now need create a Dockerfile to automate all this intallation process

### now check the history then create a step 
```ruby
root@e1465bb5f052:/opt# history
    1  apt-get install -y python
    2  apt-get update
    3  apt-get install -y python
    4  apt-get install -y python3
    5  python
    6  python3
    7  pip install flask
    8  apt-get install python3-pip
    9  pip install flask
   10  cat > /opt/app.py
   11  vi > /opt/app.py
   12  vim > /opt/app.py
   13  vim /opt/app.py
   14  nano /opt/app.py
   15  cat > /opt/app.py
   16  vi /opt/app.py
   17  FLASK_APP=app.py flask run --host=0.0.0.0
   18  cd opt/
   19  FLASK_APP=app.py flask run --host=0.0.0.0
   20  history
root@e1465bb5f052:/opt# 

### concluding these steps 

apt-get update
apt-get install -y python3
apt-get install python3-pip
pip install flask
create/copy application code to  /opt/app.py

FLASK_APP=/opt/app.py flask run --host=0.0.0.0
```

### exit from the docker engine and verify container not runnig
```ruby
root@e1465bb5f052:/opt# exit
exit
althaf@mas:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

```ruby
mkdir my-simple-webapp
cd my-simple-webapp/
cat > Dockerfile
```
### in Dockerfile
```ruby
FROM ubuntu

RUN apt-get update
RUN apt-get install -y python3 python3-pip
RUN pip install flask

COPY app.py /opt/app.py

ENTRYPOINT FLASK_APP=app.py flask run --host=0.0.0.0althaf@mas:~/my-simple-webapp
```

Ctrl+D to save and exit


```ruby
althaf@mas:~$ mkdir my-simple-webapp
althaf@mas:~$ cd my-simple-webapp/
althaf@mas:~/my-simple-webapp$ cat > Dockerfile
FROM ubuntu

RUN apt-get update
RUN apt-get install -y python3 python3-pip
RUN pip install flask

COPY app.py /opt/app.py

ENTRYPOINT FLASK_APP=app.py flask run --host=0.0.0.0althaf@mas:~/my-simple-webapp 
```

The given commands and Dockerfile are related to creating a Docker container for a simple web application. Let's break down what each part does:

1. `mkdir my-simple-webapp`: This command creates a new directory called "my-simple-webapp" in the current user's home directory. This directory will be used to store the files and code for the web application and the Dockerfile.

2. `cd my-simple-webapp/`: This command changes the current working directory to the "my-simple-webapp" directory, which was just created.

3. `cat > Dockerfile`: This command creates a new file named "Dockerfile" in the "my-simple-webapp" directory and allows you to enter text into it. The contents of this Dockerfile are used to define how the Docker container should be built.

Now, let's look at the contents of the Dockerfile:

- `FROM ubuntu`: This line specifies that the base image for the Docker container should be Ubuntu. This means that the container will be based on the Ubuntu Linux distribution.

- `RUN apt-get update`: This command updates the package list on the Ubuntu base image, ensuring that the package manager knows about the latest available packages.

- `RUN apt-get install -y python3 python3-pip`: This command installs Python 3 and pip (Python package manager) in the Docker container. The `-y` flag is used to automatically confirm the installation without asking for user input.

- `RUN pip install flask`: This command uses pip to install the Flask web framework inside the Docker container. Flask is a Python web framework used to build web applications.

- `COPY app.py /opt/app.py`: This line copies a file named "app.py" from the host system (the directory where the Dockerfile is located) to the "/opt/app.py" path within the Docker container. This assumes that there is an "app.py" file in the same directory as the Dockerfile.

- `ENTRYPOINT FLASK_APP=app.py flask run --host=0.0.0.0`: This line specifies the entry point command for the Docker container. It sets an environment variable `FLASK_APP` to "app.py" and then runs the Flask development server with the specified host "0.0.0.0." This means the Flask application will be accessible from outside the container (0.0.0.0 means all available network interfaces).

After creating this Dockerfile and building the Docker image from it, you can run a Docker container based on this image to deploy a simple web application that runs the Flask server.

### Keep in mind that you will also need an "app.py" file in the same directory as the Dockerfile, which contains your actual Flask web application code.

### create app.py file

```ruby
cat > app.py
```


```ruby
althaf@mas:~/my-simple-webapp$ cat > app.py
import os
from flask import Flask
app = Flask(__name__)

@app.route("/")
def main():
    return "Welcome!"

@app.route('/how are you')
def hello():
    return 'I am good, how about you?'

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=8080)althaf@mas:~/my-simple-webapp
althaf@mas:~/my-simple-webapp$ 

```

Ctrl+D to save the file  created through cat

# Build 
```ruby
docker build . -t my-simple-webapp
```
The command you provided, "docker build . -t my-simple-webapp," is used to create a Docker image from a Dockerfile. Let's break down the command step by step:

1. `docker build`: This part of the command instructs Docker to build an image.

2. `.`: The dot (.) represents the build context. In this context, it means that Docker should look for a Dockerfile in the current directory. The Dockerfile is a text file that contains instructions on how to create a Docker image, including what base image to use, what files to include, what packages to install, and other configuration settings.

3. `-t my-simple-webapp`: The `-t` option, followed by the image name (in this case, "my-simple-webapp"), allows you to tag the image with a name and optionally a tag. This is useful for identifying and referencing the image later. In this case, you are naming the image "my-simple-webapp."

In summary, the command "docker build . -t my-simple-webapp" tells Docker to build an image using the Dockerfile found in the current directory and tag the resulting image as "my-simple-webapp." This image can then be used to create containers for running your web application or service within a Docker environment.

```ruby 
althaf@mas:~/my-simple-webapp$ docker build . -t my-simple-webapp
[+] Building 0.1s (10/10) FINISHED                                   docker:default 
 => [internal] load .dockerignore                                              0.0s
 => => transferring context: 2B                                                0.0s
 => [internal] load build definition from Dockerfile                           0.0s
 => => transferring dockerfile: 214B                                           0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest               0.0s
 => [1/5] FROM docker.io/library/ubuntu                                        0.0s
 => [internal] load build context                                              0.0s
 => => transferring context: 28B                                               0.0s
 => CACHED [2/5] RUN apt-get update                                            0.0s
 => CACHED [3/5] RUN apt-get install -y python3 python3-pip                    0.0s
 => CACHED [4/5] RUN pip install flask                                         0.0s
 => CACHED [5/5] COPY app.py /opt/app.py                                       0.0s
 => exporting to image                                                         0.0s
 => => exporting layers                                                        0.0s
 => => writing image sha256:e65b86eb9d40b6025eedf871e5b3171cf640eaae772ec7ce6  0.0s
 => => naming to docker.io/library/my-simple-webapp                            0.0s
althaf@mas:~/my-simple-webapp$ 

```
# Run the container

```ruby
althaf@mas:~/my-simple-webapp$ docker ps
CONTAINER ID   IMAGE              COMMAND                  CREATED          STATUS          PORTS     NAMES
2ee20d674eb7   my-simple-webapp   "/bin/sh -c 'FLASK_A…"   3 minutes ago    Up 3 minutes              objective_bartik
```
```ruby
docker run my-simple-webapp
```

```ruby
althaf@mas:~/my-simple-webapp$ docker run my-simple-webapp
 * Serving Flask app '/opt/app.py'
 * Debug mode: on
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:8080
 * Running on http://172.17.0.4:8080
Press CTRL+C to quit
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 921-049-655
172.17.0.1 - - [21/Oct/2023 02:31:39] "GET / HTTP/1.1" 200 -
172.17.0.1 - - [21/Oct/2023 02:31:40] "GET /favicon.ico HTTP/1.1" 404 -
172.17.0.1 - - [21/Oct/2023 02:31:43] "GET / HTTP/1.1" 200 -
172.17.0.1 - - [21/Oct/2023 02:31:54] "GET /how%20are%20you HTTP/1.1" 200 -
172.17.0.1 - - [21/Oct/2023 02:32:09] "GET /how%20are%20you%20my%20dear HTTP/1.1" 404 -
172.17.0.1 - - [21/Oct/2023 02:32:21] "GET /how%20are%20you HTTP/1.1" 200 -

```

![Screenshot from 2023-10-21 06-36-26](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/3edbfe59-b492-4a73-b0e9-20b330fe8c4e)

![Screenshot from 2023-10-21 06-36-39](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/25f5e6c3-8359-41eb-b021-787927da33e9)

# Now the app is runnig locally .Lets push it to the Docker Hub

```ruby
docker build . -t althafofficial/my-simple-webapp
```


```ruby
althaf@mas:~/my-simple-webapp$ docker build . -t althafofficial/my-simple-webapp
 => CACHED [2/5] RUN apt-get update                                            0.0s
 => CACHED [3/5] RUN apt-get install -y python3 python3-pip                    0.0s
 => CACHED [4/5] RUN pip install flask                                         0.0s
 => CACHED [5/5] COPY app.py /opt/app.py                                       0.0s


althaf@mas:~/my-simple-webapp$ docker images
REPOSITORY                                                              TAG       IMAGE ID       CREATED        SIZE
althafofficial/my-simple-webapp                                         latest    315db2060a8f   14 hours ago   476MB
my-simple-webapp                                                        latest    e3afa2438aa6   14 hours ago   476MB
jenkins/jenkins                                                         latest    892693e4fe31   3 days ago     476MB
```
```ruby
docker push althafofficial/my-simple-webapp
```

```ruby
althaf@mas:~/my-simple-webapp$ docker push althafofficial/my-simple-webapp
denied: requested access to the resource is denied
```

```ruby
docker login
```

```ruby
althaf@mas:~/my-simple-webapp$ docker login
Log in with your Docker ID or email address to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com/ to create one.
You can log in with your password or a Personal Access Token (PAT). Using a limited-scope PAT grants better security and is required for organizations using SSO. Learn more at https://docs.docker.com/go/access-tokens/

Username: althafofficial
Password: 
WARNING! Your password will be stored unencrypted in /home/althaf/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store



Login Succeeded
althaf@mas:~/my-simple-webapp$ docker push althafofficial/my-simple-webapp
Using default tag: latest
The push refers to repository [docker.io/althafofficial/my-simple-webapp]
28d9c97a8810: Pushed 
4e4cf94e6bda: Pushed 
3d268c57ddca: Pushed 
838ff486bf53: Pushed 
256d88da4185: Mounted from library/ubuntu 
latest: digest: sha256:c64a1d347e2581083cd2f4e16531dbd2b6aa68cc2e46edf1ccf5efdbc7362da1 size: 1372
althaf@mas:~/my-simple-webapp$ 

```
# now the Application is available for public
![Screenshot from 2023-10-21 07-06-11](https://github.com/Althaf-official/KodeKloud_Docker/assets/105126131/598ecaf7-2687-4b04-8f80-d8908da38060)







