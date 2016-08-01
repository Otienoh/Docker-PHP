############################################################
# Dockerfile to build Arifu container images               #
# Based on Eboraas/apache-php                              #
############################################################

# Set the base image to Eboraas/apache-php
FROM 		eboraas/apache-php

MAINTAINER 	Otieno Julie <otienojulie@gmail.com>


RUN apt-get update && apt-get -y install git curl php5-mcrypt php5-json && apt-get -y autoremove && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN /usr/sbin/a2enmod rewrite

ADD /dockerconfigs/000-laravel.conf /etc/apache2/sites-available/
ADD /dockerconfigs/001-laravel-ssl.conf /etc/apache2/sites-available/
RUN /usr/sbin/a2dissite '*' && /usr/sbin/a2ensite 000-laravel 001-laravel-ssl

RUN /usr/bin/curl -sS https://getcomposer.org/installer |/usr/bin/php
RUN /bin/mv composer.phar /usr/local/bin/composer

# New Laravel project via git 
RUN git clone https://github.com/laravel/laravel.git
RUN /bin/chown www-data:www-data -R /var/www/laravel/storage /var/www/laravel/bootstrap/cache

WORKDIR /var/www/laravel

# Install vendor package (composer)
RUN composer install --no-interaction


EXPOSE 80
EXPOSE 443

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]