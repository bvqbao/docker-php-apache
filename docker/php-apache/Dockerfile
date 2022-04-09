FROM php:8-apache

WORKDIR /var/www

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

RUN install-php-extensions \
	gd \
	bz2 \
	intl \
	iconv \
	bcmath \
	opcache \
	calendar \
	mbstring \
	pdo_mysql \
	zip

RUN a2enmod rewrite headers

RUN chown -R www-data:www-data /var/www

USER www-data

EXPOSE 80
CMD ["apache2-foreground"]
