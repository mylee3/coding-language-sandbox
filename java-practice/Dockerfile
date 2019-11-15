# https://hub.docker.com/_/openjdk?tab=description

FROM openjdk:8

# Copying java code from local project
WORKDIR /usr/src/app
COPY java-codes .

# Keep container running for Java practice
ENTRYPOINT ["tail", "-f", "/dev/null"]
