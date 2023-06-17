FROM ubuntu:22.04

ENV TERRAFORM_VERZION 1.3.6
ENV ANSIBLE_VERSION 6.7.0
ENV DOCKER_COMPOSE 1.29.2
ENV DOCKER_ENGINE 6.0.1

ENV PATH $PATH:/usr/local/bin/terraform

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y \
    gnupg \
    software-properties-common \
    curl \
    ca-certificates \
    apt-transport-https \
    lsb-release \
    unzip \
    git \
    python3-pip && \
  echo "Install terraform ${TERRAFORM_VERZION}" && \
    curl -fsSL https://releases.hashicorp.com/terraform/${TERRAFORM_VERZION}/terraform_${TERRAFORM_VERZION}_linux_amd64.zip -o terraform.zip && \
    unzip terraform.zip && \
    mv terraform /usr/local/bin && \
  echo "Python3 dependencies" && \
    if [ ! -e /usr/bin/pip ]; then ln -s pip3 /usr/bin/pip; fi && \
    if [ ! -e /usr/bin/python ]; then ln -sf /usr/bin/python3 /usr/bin/python; fi && \
  echo "Install ansible" && \
    pip --no-cache-dir install \
      ansible==${ANSIBLE_VERSION} \
      docker==${DOCKER_ENGINE} \
      docker-compose==${DOCKER_COMPOSE} && \
  apt-get clean
