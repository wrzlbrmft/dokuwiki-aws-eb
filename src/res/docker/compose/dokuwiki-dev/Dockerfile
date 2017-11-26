FROM php:7.1-apache
EXPOSE 8080:80
RUN a2enmod rewrite
RUN apt-get update \
	&& apt-get install -y \
		libfreetype6-dev \
		libgif-dev \
		libjpeg62-turbo-dev \
		libpng12-dev \
	&& docker-php-ext-configure gd \
		--with-jpeg-dir=/usr/include \
		--with-png-dir=/usr/include \
		--with-freetype-dir=/usr/include \
	&& docker-php-ext-install gd
RUN rmdir /var/www/html \
	&& mkdir -p /var/www/src/web \
	&& ln -s /var/www/src/web /var/www/html
ADD res/dokuwiki/data.tar.gz /var/www/src/web
RUN chmod -R 0777 /var/www/src/web/data
