ARG BASE_IMAGE
FROM $BASE_IMAGE

ARG PHP_VERSION=7.4
ARG LIB_FOLDER=/usr/lib/php/20190902

RUN apt-get update && \
    apt-get -y install php${PHP_VERSION}-amqp

### Install SourceGuardian PHP module
ARG IXED=ixed.$PHP_VERSION.lin
ARG IXED_PATH=$LIB_FOLDER/$IXED
RUN wget "https://www.sourceguardian.com/loaders/download.php?d=linux-x86_64&ixed=$IXED" -O $IXED_PATH
RUN echo [sourceguardian] > /etc/php/$PHP_VERSION/mods-available/sourceguardian.ini && \
    echo extension=$IXED_PATH >> /etc/php/$PHP_VERSION/mods-available/sourceguardian.ini
RUN phpenmod -v $PHP_VERSION sourceguardian
