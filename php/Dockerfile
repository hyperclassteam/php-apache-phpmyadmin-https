FROM php:8.2-apache

# Instalare extensii PHP necesare pentru Magento 2
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libxml2-dev \
    libicu-dev \
    libxslt1-dev \
    libzip-dev \
    unzip \
    git \
    curl \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) \
    gd \
    intl \
    soap \
    xsl \
    zip \
    pdo_mysql \
    bcmath \
    opcache

# Create .ini files to enable PHP extensions
RUN echo "extension=bcmath" > /usr/local/etc/php/conf.d/docker-php-ext-bcmath.ini \
    && echo "extension=gd" > /usr/local/etc/php/conf.d/docker-php-ext-gd.ini \
    && echo "extension=intl" > /usr/local/etc/php/conf.d/docker-php-ext-intl.ini \
    && echo "zend_extension=opcache" > /usr/local/etc/php/conf.d/docker-php-ext-opcache.ini \
    && echo "extension=pdo_mysql" > /usr/local/etc/php/conf.d/docker-php-ext-pdo_mysql.ini \
    && echo "extension=soap" > /usr/local/etc/php/conf.d/docker-php-ext-soap.ini \
    && echo "extension=sodium" > /usr/local/etc/php/conf.d/docker-php-ext-sodium.ini \
    && echo "extension=xsl" > /usr/local/etc/php/conf.d/docker-php-ext-xsl.ini \
    && echo "extension=zip" > /usr/local/etc/php/conf.d/docker-php-ext-zip.ini

# Instalre sokets
RUN docker-php-ext-install sockets

# Instalare Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Setarea directorului de lucru
WORKDIR /var/www/html

#Schimbar propietar
# RUN chown -R www-data:www-data /var/www/html

# Activare module Apache necesare
RUN a2enmod rewrite

# Activare SSL
RUN a2enmod ssl && a2ensite default-ssl
