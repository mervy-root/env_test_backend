#a partir de l'image officielle de php
FROM php:8.2-apache

#installer les extensions necessaires
RUN apt-get update && apt-get install -y \
    libonig-dev \
    libzip-dev \
    zip \
    unzip \
    && docker-php-ext-install mysqli pdo_mysql mbstring

COPY ./phpmyadmin /var/www/html/
#Télécharger phpmyadmin depuis le site officiel
#RUN apt-get update && apt-get install -y wget unzip \
	#&& wget https://files.phpmyadmin.net/phpMyAdmin/5.2.2/phpMyAdmin-5.2.2-all-languages.zip \
	#&& unzip phpMyAdmin-5.2.2-all-languages.zip \
	#&& mv phpMyAdmin-5.2.2-all-languages.zip /var/www/html/phpmyadmin \
	#&& rm phpMyAdmin-5.2.2-all-languages.zip

#Copier le fichier de configuration phpMyAdmin
COPY config.inc.php /var/www/html/phpmyadmin/config.inc.php

#Configurer le serveur
RUN chown -R www-data:www-data /var/www/html/phpmyadmin

#Active la reecriture d'URL d'apache si besoin
RUN a2enmod rewrite

#ouvrir le port http
EXPOSE 80

