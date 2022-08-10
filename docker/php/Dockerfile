FROM php:7.4-cli

# Install SUPERVISOR
RUN apt-get update \
    && apt-get install -y supervisor \
    && apt-get install -y procps \
    && apt-get install -y zip unzip telnet\
    && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install -j$(nproc) \
        bcmath

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set USER
RUN useradd -ms /bin/bash project && adduser project sudo
USER project
WORKDIR /home/project/app
