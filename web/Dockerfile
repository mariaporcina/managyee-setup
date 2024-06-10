FROM php:8.1-apache
ENV TZ=America/Sao_Paulo
RUN docker-php-ext-install mysqli
RUN rm -Rf /var/www/html/
COPY ./www /var/www/html/
