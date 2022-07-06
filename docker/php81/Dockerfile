FROM php:8.1-apache-buster

ARG DEBIAN_FRONTEND=noninteractive

# Install useful tools and install important libaries
RUN apt-get -y update --fix-missing && apt-get upgrade -y && \
	apt-get -y --no-install-recommends install apt-utils nano wget git curl openssl && \
	apt-get -y --no-install-recommends install --fix-missing libcurl4 libcurl4-openssl-dev libonig-dev && \
	apt-get -y --no-install-recommends install libpng-dev libjpeg62-turbo-dev && \

# Install unzip utility and libs needed by zip PHP extension 
	apt-get -y install zlib1g-dev libzip-dev unzip && \

# Download and install composer
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \

# Download browscap.ini
	mkdir /var/lib/browscap && wget http://browscap.org/stream?q=BrowsCapINI -O /var/lib/browscap/browscap.ini	

# Other PHP8 Extensions
RUN docker-php-ext-install pdo_mysql && \
    docker-php-ext-install mysqli && \
    docker-php-ext-install curl && \
	docker-php-ext-install mbstring && \
    docker-php-ext-install gettext && \
    docker-php-ext-install gd && \
	docker-php-ext-install zip && \
	docker-php-ext-install opcache

# Enable apache modules
RUN a2enmod rewrite headers

# Cleanup
RUN apt-get clean -y && rm -rf /usr/src/*