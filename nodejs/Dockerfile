FROM debian:trixie

RUN  apt-get update && \
  apt-get upgrade -y && \
  apt-get install -y \
  make \
  curl \
  git && \
  curl -fsSL https://deb.nodesource.com/setup_24.x | bash - && \
  apt-get update && \
  apt-get install -y \
  nodejs

RUN npm install -g yarn pnpm