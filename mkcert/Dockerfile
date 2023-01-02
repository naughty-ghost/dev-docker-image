# コードを実行するコンテナイメージ
FROM ubuntu:latest

WORKDIR /Cert
RUN apt update && \
    apt install -y \
        libnss3-tools \
        curl \
        git
RUN curl -JLO "https://dl.filippo.io/mkcert/latest?for=linux/amd64" && \
  chmod +x mkcert-v*-linux-amd64 && \
  cp mkcert-v*-linux-amd64 /usr/local/bin/mkcert