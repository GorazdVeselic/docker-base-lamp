FROM php:7.4.3-apache

LABEL maintainer="gorazd@spletnakoda.si"
LABEL description="Apache / PHP for dev"

# to be able to use "nano" with shell on "docker exec -it [CONTAINER ID] bash"
ENV TERM xterm

ARG USER_ID=1000
ARG GROUP_ID=1001

RUN userdel -f www-data &&\
    if getent group www-data ; then groupdel www-data; fi &&\
    groupadd -g ${GROUP_ID} www-data &&\
    useradd -l -u ${USER_ID} -g www-data www-data &&\
    install -d -m 0755 -o www-data -g www-data /home/www-data

RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN a2enmod rewrite

USER root

RUN chgrp -R www-data /var/www

RUN mkdir -p /var/www/html/logs
RUN chmod a+rw -R /var/www/html/logs/

RUN rm -rf /var/www/html/storage/templates_c
RUN mkdir -p /var/www/html/storage/templates_c
RUN chmod a+rw -R /var/www/html/storage/templates_c/

RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

# for production :
# RUN echo "ServerTokens Prod\n" >> /etc/apache2/apache2.conf
# RUN echo "ServerSignature Off\n" >> /etc/apache2/apache2.conf

# Set working directory
WORKDIR /var/www/html

EXPOSE 80
