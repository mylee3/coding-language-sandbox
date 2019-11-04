# python-practice

This sets up the development environment for Python 3 code.

## Python environment Dockerfile

The Dockerfile for Python 3 builds an image based on Ubuntu 16.04

```
# https://gist.github.com/monkut/c4c07059444fd06f3f8661e13ccac619

FROM ubuntu:16.04

# Installing Python 3.6
RUN apt-get update && \
  apt-get install -y software-properties-common && \
  add-apt-repository ppa:jonathonf/python-3.6 && \
  apt-get update && \
  apt-get install -y build-essential python3.6 python3.6-dev python3-pip python3.6-venv

# Copying python code from local project
WORKDIR /usr/src/app
COPY python-codes .

# Keep container running for Python practice
ENTRYPOINT ["tail", "-f", "/dev/null"]

```

First it installs the neccessary packages for Python3.6, then copies the Python files from the local project.  The last line keeps the container running for the Python environment.

## Building and running the Docker Python container

Build the image with "docker image build".

```
$ cd python-practice
$ sudo docker image build -t python-project:0.0.1 .
```

Then run the new python image with "docker run".

```
$ sudo docker container run --detach --name python-project python-project:0.0.1
```

Check that the container with the name "python-project" is running:

```
$ sudo docker ps -a

CONTAINER ID        IMAGE                  COMMAND               CREATED              STATUS                       PORTS               NAMES
31797cc193ab        python-project:0.0.1   "tail -f /dev/null"   About a minute ago   Exited (137) 9 seconds ago                       python-project

```

You can then enter the container with "docker exec"

```
$ sudo docker exec -ti python-project bash

root@31797cc193ab:/usr/src/app# 

```

The Python code from the local project can be found inside the container.

```
root@31797cc193ab:/usr/src/app# python-examples

root@31797cc193ab:/usr/src/app# ls
hello_world.py

root@31797cc193ab:/usr/src/app# python3 hello_world.py
Hello world!

```

Exit out of the running container anytime.

```
root@31797cc193ab:/usr/src/app# exit

$ 

```

## Cleaning up the Python container

When you are done with the environment, you can stop and remove the Python container.

```
$ sudo docker stop python-project
python-project

$ sudo docker remove python-project
python-project

```

The Python container should be removed.

```
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES

```