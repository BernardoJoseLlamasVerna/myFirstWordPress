FROM wordpress:php7.2-apache

COPY ./wordpress.php.ini /usr/local/etc/php/conf.d/wordpress.php.ini

# XDEBUG Install and config
#RUN yes | pecl install xdebug \
#    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
#    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
#    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini

# Installing packages
RUN apt-get update && apt-get install -y \
        git \
        zip \
        unzip \
        curl \
        gnupg

# Install wp-cli
RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar && \
    chmod +x wp-cli.phar && \
    mv wp-cli.phar /usr/local/bin/wp

# Install requirements for wp-cli support
RUN apt-get update && \
    apt-get install -y sudo less mariadb-client