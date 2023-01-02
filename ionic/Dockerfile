FROM node:18.12

RUN apt update && \
    apt install -y \
        curl \
        xsel && \
    npm install -g \
        @ionic/cli \
        serve

CMD [ "bash" ]