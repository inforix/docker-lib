# from https://www.drupal.org/docs/8/system-requirements/drupal-8-php-requirements
FROM drupal:7.69-apache

# install imagemagick and uploadprogress
RUN set -eux; \
	apt-get update && apt-get install -y imagemagick libmagickwand-dev libmagickcore-dev --no-install-recommends \
  && pecl install imagick \
  && docker-php-ext-enable imagick \
  && pecl install uploadprogress \
  && docker-php-ext-enable uploadprogress