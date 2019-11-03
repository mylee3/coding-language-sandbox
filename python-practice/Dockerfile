# https://gist.github.com/monkut/c4c07059444fd06f3f8661e13ccac619

FROM ubuntu:16.04

# Installing Python 3.6
RUN apt-get update && \
  apt-get install -y software-properties-common && \
  add-apt-repository ppa:jonathonf/python-3.6
RUN apt-get update

RUN apt-get install -y build-essential python3.6 python3.6-dev python3-pip python3.6-venv

# Copying python code from local project
WORKDIR /usr/src/app
COPY python-codes .
