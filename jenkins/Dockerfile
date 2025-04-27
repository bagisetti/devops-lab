FROM jenkins/jenkins:lts

USER root

RUN apt-get update && apt-get install -y \
    zip \
    unzip \
    awscli \
    docker.io

USER jenkins
