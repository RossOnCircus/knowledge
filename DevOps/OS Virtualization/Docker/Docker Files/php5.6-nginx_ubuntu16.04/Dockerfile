FROM ubuntu:16.04
LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"
COPY site-nginx.conf composer-install.sh /tmp/
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
    php-gd \
    nginx \
    php5.6 \
    php5.6-fpm \
    php5.6-mbstring \
    php5.6-curl \
    php5.6-mcrypt \
    php5.6-tokenizer \
    php5.6-dom \
    php5.6-zip \
    php5.6-mysql \
    php5.6-imap \
    php5.6-xml \
    php5.6-cli \
    php5.6-gd \
    php5.6-intl && \
    mv /tmp/site-nginx.conf /etc/nginx/sites-available/ && \
    mv /tmp/composer-install.sh /var/www/composer-install.sh && \
    ln -s /etc/nginx/sites-available/site-nginx.conf /etc/nginx/sites-enabled/site && \
    chown -R www-data:www-data /var/www && \ 
    find /var/www -type d -exec chmod 755 {} \; && \
    find /var/www -type f -exec chmod 644 {} \; && \
    echo "\ndaemon off;" >> /etc/nginx/site-nginx.conf && \
    sed -i -e "s/;\?daemonize\s*=\s*yes/daemonize = no/g" /etc/php/5.6/fpm/php-fpm.conf && \
    echo "\ncgi.fix_pathinfo = 0" >> /etc/php/5.6/fpm/php.ini && \
    echo "\nfile_uploads = On" >> /etc/php/5.6/fpm/php.ini && \
    echo "\nallow_url_fopen = On" >> /etc/php/5.6/fpm/php.ini && \
    echo "\nmemory_limit = 512M" >> /etc/php/5.6/fpm/php.ini && \
    echo "\nmax_execution_time = 360" >> /etc/php/5.6/fpm/php.ini && \
    echo "\nupload_max_filesize = 100M" >> /etc/php/5.6/fpm/php.ini && \
    echo "\npost_max_size = 100M" >> /etc/php/5.6/fpm/php.ini && \
    echo "\ndate.timezone = Asia\/Manila" >> /etc/php/5.6/fpm/php.ini && \
    chmod +x /var/www/composer-install.sh && \
    sh /var/www/composer-install.sh && \
    rm /var/www/composer-install.sh
EXPOSE 80
ENTRYPOINT ["/bin/bash"]
