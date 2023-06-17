FROM ubuntu:22.04

RUN  apt-get update && \
  apt-get upgrade -y && \
  apt-get install -y \
  make \
  curl \
  git && \
  curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && \
  apt-get update && \
  apt-get install -y \
  nodejs

RUN npm install -g yarn