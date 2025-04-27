FROM node:20-bullseye

USER root

# Install Java, Python 3 and pip and curl
RUN apt-get update && \
    apt-get install -y \
    openjdk-17-jre \
    python3 \
    python3-pip \
    curl

# Download Jenkins agent jar
RUN mkdir -p /home/jenkins/agent

# Set working directory
WORKDIR /home/jenkins/agent