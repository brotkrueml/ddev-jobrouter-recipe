ARG BASE_IMAGE
FROM $BASE_IMAGE

ARG PHP_VERSION=7.4
ARG LIB_FOLDER=/usr/lib/php/20190902

### Install AMQP PHP module and dependencies
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -qq install -o Dpkg::Options::="--force-confnew" --no-install-recommends --no-install-suggests -y \
    autoconf \
    gcc \
    libc-dev \
    librabbitmq4 \
    librabbitmq-dev \
    make \
    pkg-config \
    php-pear \
    php${PHP_VERSION}-dev 
RUN pecl channel-update pecl.php.net
RUN echo | pecl install amqp
RUN echo [PHP] > /etc/php/$PHP_VERSION/mods-available/amqp.ini && \
    echo extension=amqp.so >> /etc/php/$PHP_VERSION/mods-available/amqp.ini
RUN phpenmod -v $PHP_VERSION amqp

### Install SourceGuardian PHP module
ARG IXED=ixed.$PHP_VERSION.lin
ARG IXED_PATH=$LIB_FOLDER/$IXED
RUN wget "https://www.sourceguardian.com/loaders/download.php?d=linux-x86_64&ixed=$IXED" -O $IXED_PATH
RUN echo [sourceguardian] > /etc/php/$PHP_VERSION/mods-available/sourceguardian.ini && \
    echo extension=$IXED_PATH >> /etc/php/$PHP_VERSION/mods-available/sourceguardian.ini
RUN phpenmod -v $PHP_VERSION sourceguardian
