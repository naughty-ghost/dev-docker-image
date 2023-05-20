FROM ghcr.io/ms-naughty-ghost/dev-docker-image-nodejs:0.2.0

RUN apt update && \
    apt install -y \
        curl \
        xsel && \
    npm install -g \
        @ionic/cli \
        serve

CMD [ "bash" ]