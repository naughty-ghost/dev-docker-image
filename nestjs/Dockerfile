FROM ghcr.io/ms-naughty-ghost/dev-docker-image-nodejs:0.2.0

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y procps && \
    npm i -g @nestjs/cli