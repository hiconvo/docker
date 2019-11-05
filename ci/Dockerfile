# Installs JRE, Go, Node, GCloud SDK, and other build essentails in
# a stretch environment.
FROM debian:stretch

WORKDIR /tmp

# Install essentails
RUN apt-get update
RUN apt-get install -y \
  apt-transport-https \
  ca-certificates \
  curl \
  gnupg2 \
  software-properties-common \
  build-essential

# Add keys
RUN curl -sSL https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add -
RUN curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -

# Add sources
RUN echo "deb https://deb.nodesource.com/node_10.x stretch main" | tee /etc/apt/sources.list.d/nodesource.list
RUN echo "deb-src https://deb.nodesource.com/node_10.x stretch main" | tee -a /etc/apt/sources.list.d/nodesource.list
RUN echo "deb http://packages.cloud.google.com/apt cloud-sdk-stretch main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list

# Install
RUN apt-get update
RUN apt-get install -y \
  git-all \
  nodejs \
  google-cloud-sdk \
  google-cloud-sdk-app-engine-go

# Install Go, which is not available via apt
RUN curl -O "https://dl.google.com/go/go1.13.4.linux-amd64.tar.gz"
RUN tar -C /usr/local -xzf go1.13.4.linux-amd64.tar.gz
RUN rm go1.13.4.linux-amd64.tar.gz
ENV PATH="${PATH}:/usr/local/go/bin"
