FROM composer AS composer


FROM php:8.2-apache

COPY --from=composer /usr/bin/composer /usr/bin/composer
COPY . .

RUN apt-get update \
    && apt-get install -y \
    libicu-dev libzip-dev \
    && docker-php-ext-install pdo_mysql intl zip -j$(nproc) \
    && docker-php-ext-enable opcache \
    && apt-get autoclean -y \
    && rm -rf /var/lib/apt/lists/*

RUN apt-get update \
    && apt-get install -y "$(cat add_pkgs | head -n 1)" || true \
    && docker-php-ext-install "$(cat install_ext | head -n 1)" || true \
    && docker-php-ext-enable "$(cat enable_ext | head -n 1)" || true \
    && apt-get autoclean -y \
    && rm -rf /var/lib/apt/lists/* \

# Update apache config to point to the *public* directory
ENV APACHE_DOCUMENT_ROOT=/var/www/public
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf

# Enable headers module
RUN a2enmod rewrite headers
