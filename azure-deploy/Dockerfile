FROM ubuntu:22.04

ENV TERRAFORM_VERZION 1.6.4
ENV ANSIBLE_VERSION 9.0.1
ENV AZURE_CLI=2.44.1

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
      PyYAML==5.3.1 \
      ansible==${ANSIBLE_VERSION} && \
  echo "Install AZURE CLI" && \
    pip --no-cache-dir install azure-cli==${AZURE_CLI} && \
  echo "Install Docker Engine" && \
    mkdir -m 0755 -p /etc/apt/keyrings && \
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg && \
    chmod a+r /etc/apt/keyrings/docker.gpg && \
    echo \
        "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
        $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null && \
    apt-get update && \
    apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin && \
  apt-get clean
