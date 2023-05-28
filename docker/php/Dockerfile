FROM php:8.2.6RC1-fpm
ARG LINUX_USER
ENV LINUX_USER=${LINUX_USER}
RUN apt-get update && apt-get install -y \
    && apt-get -y install sudo \
    && apt-get -y install apt-transport-https \
    && apt-get -y install gnupg \
# symfony related commands
    && sudo apt-get install -y libicu-dev unzip  \
    && docker-php-ext-install intl \
    && docker-php-ext-install opcache \
    && curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | sudo -E bash \
    && apt -y install symfony-cli
# end symfony related commands
COPY --from=composer/composer:latest-bin /composer /usr/bin/composer
RUN groupadd -r php \
    && useradd -r -g php ${LINUX_USER}  \
    && mkdir /home/${LINUX_USER}  \
    && chown -R ${LINUX_USER}:php /home/${LINUX_USER}  \
    && chown -R ${LINUX_USER}:php /var/www/html
USER ${LINUX_USER}
WORKDIR /var/www/html