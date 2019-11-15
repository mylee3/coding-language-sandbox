# https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04

FROM ubuntu:16.04

# Installing Java 8
RUN apt-get update
# RUN apt-get install default-jre
# RUN apt-get install default-jdk
# RUN add-apt-repository ppa:webupd8team/java
# RUN apt-get update
# RUN apt-get install oracle-java8-installer

# Copying java code from local project
WORKDIR /usr/src/app
COPY java-codes .

# Keep container running for Java practice
ENTRYPOINT ["tail", "-f", "/dev/null"]
