FROM php:7.4-cli-alpine

LABEL \
	maintainer="Toofff <toofff.development@gmail.com>"

RUN set -e -u -x \
\
	# Install packages
\
	&& apk add --no-cache --no-progress --virtual BUILD_DEPS ${PHPIZE_DEPS} \
	&& apk add --no-cache --no-progress tzdata \
\
	# Install php-ext-amqp
\
	&& apk add --no-cache --no-progress --virtual BUILD_DEPS_PHP_AMQP rabbitmq-c-dev \
	&& apk add --no-cache --no-progress rabbitmq-c \
	&& pecl install amqp \
	&& docker-php-ext-enable amqp \
\
	# Install php-ext-apcu
\
	&& pecl install apcu \
	&& docker-php-ext-enable apcu \
\
	# Install php-ext-apfd
\
	&& pecl install apfd \
	&& docker-php-ext-enable apfd \
\
	# Install php-ext-exif
\
	&& docker-php-ext-install exif \
\
	# Install php-ext-gd
\
	&& apk add --no-cache --no-progress --virtual BUILD_DEPS_PHP_GD freetype-dev libjpeg-turbo-dev libpng-dev \
	&& apk add --no-cache --no-progress freetype libjpeg-turbo libpng \
	&& docker-php-ext-configure gd --with-freetype --with-jpeg \
	&& docker-php-ext-install gd \
\
	# Install php-ext-imagick
\
	&& apk add --no-cache --no-progress --virtual BUILD_DEPS_PHP_IMAGICK imagemagick-dev \
	&& apk add --no-cache --no-progress imagemagick \
	&& pecl install imagick \
	&& docker-php-ext-enable imagick \
\
	# Install php-ext-intl
\
	&& apk add --no-cache --no-progress --virtual BUILD_DEPS_PHP_INTL icu-dev \
	&& apk add --no-cache --no-progress icu \
	&& docker-php-ext-install intl \
\
	# Install php-ext-opcache
\
	&& docker-php-ext-install opcache \
\
	# Install php-ext-mysql
\
	&& docker-php-ext-install pdo_mysql \
\
	# Install php-ext-pgsql
\
	&& apk add --no-cache --no-progress --virtual BUILD_DEPS_PHP_PGSQL postgresql-dev \
	&& apk add --no-cache --no-progress postgresql-libs \
	&& docker-php-ext-install pdo_pgsql pgsql \
\
	# Install php-ext-redis
\
	&& pecl install redis \
	&& docker-php-ext-enable redis \
\
	# Install php-ext-xdebug
\
	&& pecl install xdebug \
\
	# Install php-ext-xml
\
	&& apk add --no-cache --no-progress --virtual BUILD_DEPS_PHP_XML libxml2-dev \
	&& apk add --no-cache --no-progress libxml2 \
	&& docker-php-ext-install xml \
\
	# Install php-ext-xsl
\
	&& apk add --no-cache --no-progress --virtual BUILD_DEPS_PHP_XSL libxslt-dev \
	&& apk add --no-cache --no-progress libxslt \
	&& docker-php-ext-install xsl \
\
	# Install php-ext-zip
\
	&& apk add --no-cache --no-progress --virtual BUILD_DEPS_PHP_ZIP libzip-dev \
	&& apk add --no-cache --no-progress libzip \
	&& docker-php-ext-install zip \
\
	# Clean
\
	&& apk del --no-progress BUILD_DEPS BUILD_DEPS_PHP_AMQP BUILD_DEPS_PHP_GD BUILD_DEPS_PHP_IMAGICK BUILD_DEPS_PHP_INTL BUILD_DEPS_PHP_PGSQL BUILD_DEPS_PHP_XML BUILD_DEPS_PHP_XSL BUILD_DEPS_PHP_ZIP \
	&& rm -f -r /tmp/*
