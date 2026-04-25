FROM debian:trixie

ENV GO_VERSION=1.26.2

ENV PATH=$PATH:/usr/local/go/bin:/root/go/bin

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y \
    curl \
    git \
    make && \
    curl -fsSL https://go.dev/dl/go${GO_VERSION}.linux-amd64.tar.gz -o go.tar.gz && \
    tar -C /usr/local -xzf go.tar.gz && \
    rm go.tar.gz && \
    apt-get clean && \
    go install github.com/air-verse/air@latest
