FROM php:8.2.6RC1-fpm
RUN apt-get update && apt-get install -y \
    && apt-get -y install sudo \
    && apt-get -y install apt-transport-https \
    && apt-get -y install gnupg \
    && curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | sudo -E bash \
    && apt -y install symfony-cli
WORKDIR /