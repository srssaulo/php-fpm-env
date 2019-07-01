FROM php:7.2-fpm
# RUN docker-php-ext-install pgsql && \
RUN  echo "Install php extentions >>>>" &&\    
    apt-get update && \
    apt-get install -y \
    libzip-dev  \
    zip \
    unzip \
    libpq-dev \    
    libicu-dev \
    g++ \
    && docker-php-ext-configure zip --with-libzip \
    && docker-php-ext-install zip \
    && docker-php-ext-install pdo pdo_pgsql \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl



# COPY ./php/opcache.ini /usr/local/etc/php/conf.d/opcache.ini

# RUN echo "Install INTL >>>>>>" &&\
#     apt-get install -y zlib1g-dev libicu-dev g++ && \
#     docker-php-ext-install intl \

RUN  echo "Create devuser >>>>>>" &&\
     adduser -u 1000 devuser && \
     chown -R devuser:devuser /var/www && \
     chown -R devuser:devuser /home/devuser



COPY ./composer/composer.phar /usr/local/bin

RUN mv /usr/local/bin/composer.phar /usr/local/bin/composer && \
    chown -R devuser:devuser /usr/local/bin/composer && \
    chmod 770 /usr/local/bin/composer

WORKDIR "/var/www/html"

USER devuser