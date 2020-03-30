# from https://www.drupal.org/docs/8/system-requirements/drupal-8-php-requirements
FROM drupal:7.69-apache

# install the PHP extensions we need
RUN set -eux; \
	apt-get update && apt-get install -y imagemagick libmagickwand-dev libmagickcore-dev --no-install-recommends \
  && pecl install imagick \
  && docker-php-ext-enable imagick \
  && rm -rf /var/lib/apt/lists/*

# Uploadprogress
RUN mkdir -p /usr/src/php/ext/uploadprogress && \
  curl -fsSL "https://github.com/php/pecl-php-uploadprogress/archive/uploadprogress-1.1.3.tar.gz" | tar xz --strip-components=1 -C /usr/src/php/ext/uploadprogress && \
  docker-php-ext-configure uploadprogress && \
  docker-php-ext-install uploadprogress && \
  rm -rf \
      /usr/src/php/ext/uploadprogress \
      /tmp/*