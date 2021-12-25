FROM composer:latest as build 
WORKDIR /app 
COPY /src/laravel-8.6.5 /app
RUN composer install

FROM php:8.0-apache 
EXPOSE 80 
COPY --from=build /app /app 
COPY build/vhost.conf /etc/apache2/sites-available/000-default.conf 
RUN chown -R www-data:www-data /app \ 
  && a2enmod rewrite
