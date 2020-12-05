FROM php:7.2-fpm

# php default extensions
RUN apt-get update \
    && apt-get install -y libmemcached-dev  libmemcached11 zlib1g-dev gnupg2\
    && docker-php-ext-install pdo pdo_mysql \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && pecl install memcached \
    && docker-php-ext-enable memcached \
    && pecl install memcache \
    && docker-php-ext-enable memcache \ 
    && docker-php-ext-install mysqli


#mssql extensions
RUN apt-get install -y gnupg2 \
    && curl -s https://packages.microsoft.com/keys/microsoft.asc | apt-key add - \
    && bash -c "curl -s https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list" \
    && apt-get update \
    && ACCEPT_EULA=Y apt-get -y install msodbcsql17 mssql-tools \
    && apt-get -y install unixodbc-dev \
    && pecl install sqlsrv \
    && docker-php-ext-enable sqlsrv \
    && pecl install pdo_sqlsrv \
    && docker-php-ext-enable pdo_sqlsrv