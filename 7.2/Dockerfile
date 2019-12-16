FROM php:7.2

RUN additionalPackages=" \
        subversion \
    " \
    buildDeps=" \
        zlib1g-dev \
    " \
    && phpModules=" \
        mysqli \
        pdo_mysql \
        zip" \ 
    && apt-get update \
    && apt-get install -y --no-install-recommends $additionalPackages $buildDeps \
    && docker-php-ext-install $phpModules \
    && apt-get clean

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer


# Install phpunit and put binary into $PATH
RUN curl -sSLo phpunit.phar https://phar.phpunit.de/phpunit-7.phar \
    && chmod 755 phpunit.phar \
    && mv phpunit.phar /usr/local/bin/ \
    && ln -s /usr/local/bin/phpunit.phar /usr/local/bin/phpunit

CMD ["php", "-a"]