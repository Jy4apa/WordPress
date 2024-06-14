FROM wordpress:6

# Install modules
RUN apt-get update && apt-get install -y \
    wget

RUN pecl install -o -f xdebug \
    && rm -rf /tmp/pear

COPY ./install-composer.sh /

RUN apt-get purge -y g++ \
    && apt-get autoremove -y \
    && rm -r /var/lib/apt/lists/* \
    && rm -rf /tmp/* \
    && sh /install-composer.sh \
    && rm /install-composer.sh

RUN usermod -u 1000 www-data

VOLUME /root/.composer
WORKDIR /var/www/html
