FROM php:8.1-apache

# Install required PHP extensions for database connectivity
RUN docker-php-ext-install pdo pdo_mysql

# Enable Apache mod_rewrite for custom route handling
RUN a2enmod rewrite

# Configure Apache document root to point to the /public directory
ENV APACHE_DOCUMENT_ROOT /var/www/html/public
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/conf-available/*.conf

# Copy all repository files into the container
COPY . /var/www/html/

EXPOSE 80
