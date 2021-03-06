FROM ubuntu:16.04
LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"
COPY apache-config.conf composer-install.sh /tmp/
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends software-properties-common python-software-properties && \
    LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php && \
    apt-get update -y && \
    apt-get install -y --no-install-recommends \
    wget \
    curl \
    zip \
    vim \
    wkhtmltopdf \
    libxrender1 \
    git \
    cron \
    openssl \
    apt-utils \
    lynx-cur \
    php-xdebug \
    php-ast \
    php-gd \
    libapache2-mod-php7.2 \
    apache2 \
    php7.2 \
    php7.2-fpm \
    php7.2-mbstring \
    php7.2-curl \
    php7.2-tokenizer \
    php7.2-dom \
    php7.2-zip \
    php7.2-mysql \
    php7.2-imap \
    php7.2-xml \
    php7.2-cli \
    php7.2-gd \
    php7.2-intl && \
    mv /tmp/apache-config.conf /etc/apache2/sites-enabled/000-default.conf && \
    mv /tmp/composer-install.sh /var/www/composer-install.sh && \
    a2enmod php7.2 && \
    a2enconf php7.2-fpm && \
    a2enmod rewrite && \
    a2enmod headers && \
    cp /usr/lib/php/7.2/php.ini-development /etc/php/7.2/apache2 && \
    mv /etc/php/7.2/apache2/php.ini /etc/php/7.2/apache2/php.ini.bak && \
    mv /etc/php/7.2/apache2/php.ini-development /etc/php/7.2/apache2/php.ini && \
    sed -i "s/short_open_tag = /short_open_tag = Off/" /etc/php/7.2/apache2/php.ini && \
    sed -i "s/date.timezone = ;/date.timezone = Asia\/Manila/" /etc/php/7.2/apache2/php.ini && \
    sed -i "s/error_reporting = .*$/error_reporting = E_ERROR | E_WARNING | E_PARSE/" /etc/php/7.2/apache2/php.ini && \
    echo "ServerName localhost" >> /etc/apache2/apache2.conf && \
    chown -R www-data:www-data /var/www && \ 
    find /var/www -type d -exec chmod 755 {} \; && \
    find /var/www -type f -exec chmod 644 {} \; && \
    chmod +x /var/www/composer-install.sh && \
    sh /var/www/composer-install.sh && \
    rm /var/www/composer-install.sh
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid
EXPOSE 80
ENTRYPOINT ["/bin/bash"]
