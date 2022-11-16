ARG BASE_IMAGE
FROM $BASE_IMAGE

ARG PHP_VERSION=8.1
ARG LIB_FOLDER=/usr/lib/php/20210902

### Install AMQP PHP module and dependencies
RUN apt-get update && \
    apt-get -y install php${PHP_VERSION}-amqp

### Install SourceGuardian PHP module
ARG IXED=ixed.$PHP_VERSION.lin
ARG IXED_PATH=$LIB_FOLDER/$IXED
RUN wget --user-agent="Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:107.0) Gecko/20100101 Firefox/107.0" "https://www.sourceguardian.com/loaders/download.php?d=linux-x86_64&ixed=$IXED" -O $IXED_PATH
RUN echo [sourceguardian] > /etc/php/$PHP_VERSION/mods-available/sourceguardian.ini && \
    echo extension=$IXED_PATH >> /etc/php/$PHP_VERSION/mods-available/sourceguardian.ini
RUN phpenmod -v $PHP_VERSION sourceguardian
