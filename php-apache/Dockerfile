###########################################################
# Fichier définissant une image Docker
# docs : https://docs.docker.com/engine/reference/builder/
###########################################################

# Image sur laquelle se baser
FROM php:5.6-apache

# configuration de PHP
COPY config/php.ini /usr/local/etc/php/
# configuration d'apache
COPY config/vhosts/ /etc/apache2/sites-enabled/

# installation des extensions PHP
RUN docker-php-ext-install pdo_mysql
