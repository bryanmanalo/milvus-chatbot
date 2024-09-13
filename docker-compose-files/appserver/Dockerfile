FROM php:8.2-apache

# Install necessary packages and tools
RUN apt-get update && apt-get install -y \
    curl \
    git \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# Install PDO MySQL extension
RUN docker-php-ext-install pdo_mysql

RUN apt-get update && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
  && docker-php-ext-configure gd --with-freetype --with-jpeg \
  && docker-php-ext-install gd

# Install Composer globally
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Enable Apache mod_rewrite if needed (optional)
RUN a2enmod rewrite

# Set the document root if using something other than /var/www/html (optional)
# RUN sed -i 's|/var/www/html|/var/www/docroot|g' /etc/apache2/sites-available/000-default.conf
