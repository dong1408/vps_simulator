FROM gitlab/gitlab-runner:latest

RUN apt-get update && \
    apt-get install -y curl && \
    curl -fsSL https://get.docker.com | sh

RUN usermod -aG root gitlab-runner