# from https://www.drupal.org/docs/8/system-requirements/drupal-8-php-requirements
FROM drupal:7.73-apache

# install imagemagick and uploadprogress
RUN set -eux; \
	apt-get update && apt-get install -y imagemagick libmagickwand-dev libmagickcore-dev --no-install-recommends \
  && pecl install imagick \
  && docker-php-ext-enable imagick
#  && pecl install uploadprogress \
#  && docker-php-ext-enable uploadprogress

RUN ln -sf //etc/apache2/mods-available/headers.load /etc/apache2/mods-enabled/headers.load
COPY .htaccess /var/www/html/.htaccess
