# Base image on Ubuntu 18.04 LTS
FROM ubuntu:18.04

# Install essential Linux packages.
ADD ./ruby-versions.txt /root/ruby-versions.txt
RUN export PATH=/root/.rbenv/bin:$PATH && \
    apt-get update -qq && \
    apt-get install -y --no-install-recommends \
    ca-certificates \
    git \
    build-essential \
    curl \
    libpq-dev \
    default-libmysqlclient-dev \
    cmake \
    gnupg \
    pkg-config \
    xvfb \
    openssh-client \
    libxslt1-dev \
    libxml2-dev \
    zlib1g-dev \
    libssl-dev \
    libreadline-dev \
    libyaml-dev \
    libmagickwand-dev \
    imagemagick \
    libmagickcore-dev \
    bash && \
    curl -sL https://deb.nodesource.com/setup_11.x | bash - && \
    apt-get install -y --no-install-recommends nodejs && \
    git config --global http.sslverify false && \
    echo insecure >> /root/.curlrc\ && \
    git clone https://github.com/rbenv/rbenv.git /root/.rbenv && \
    git clone https://github.com/rbenv/ruby-build.git /root/.rbenv/plugins/ruby-build && \
    /root/.rbenv/plugins/ruby-build/install.sh && \
    echo 'eval "$(rbenv init -)"' >> /etc/profile.d/rbenv.sh && \
    echo 'eval "$(rbenv init -)"' >> ~/.bashrc && \
    export CONFIGURE_OPTS=--disable-install-doc && \
    xargs -L 1 rbenv install < /root/ruby-versions.txt
