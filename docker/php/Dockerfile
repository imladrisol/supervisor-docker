FROM php:7.4-cli

# Install SUPERVISOR
RUN apt-get update \
    && apt-get install -y supervisor \
    && apt-get install -y procps \
    && rm -rf /var/lib/apt/lists/*

# Set USER
RUN useradd -ms /bin/bash project && adduser project sudo
USER project
WORKDIR /home/project/app
