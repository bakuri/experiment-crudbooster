FROM php:7.1.2-apache 
RUN apt-get -y update --fix-missing
RUN apt-get upgrade -y
RUN apt-get update \
    && apt-get install -y git zlib1g-dev wget curl libcurl3 libmcrypt-dev libpng* \
    && docker-php-ext-install mcrypt pdo gd gettext mbstring tokenizer pdo_mysql zip mysqli

RUN curl -sS https://getcomposer.org/installer \
  | php -- --install-dir=/usr/local/bin --filename=composer
COPY ./website.conf  /etc/apache2/sites-available/
COPY ./hosts  /etc/hosts
RUN a2enmod rewrite    
WORKDIR /etc/apache2/sites-available/
RUN a2ensite website.conf 
RUN service apache2 restart
