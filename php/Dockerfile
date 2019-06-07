FROM php:7.2-fpm
RUN docker-php-ext-install mysqli pdo_mysql
RUN  echo "Create devuser >>>>>>" &&\
     adduser -u 1000 devuser && \
     chown -R devuser:devuser /var/www && \
     chown -R devuser:devuser /home/devuser

RUN  echo "Install php extentions >>>>" &&\
    apt-get update && \
    apt-get install -y \
    libzip-dev  \
    zip \
    unzip \
    && docker-php-ext-configure zip --with-libzip \
    && docker-php-ext-install zip


COPY ./composer/composer.phar /usr/local/bin

RUN mv /usr/local/bin/composer.phar /usr/local/bin/composer && \
    chown -R devuser:devuser /usr/local/bin/composer && \
    chmod 770 /usr/local/bin/composer

WORKDIR "/var/www/html"

USER devuser