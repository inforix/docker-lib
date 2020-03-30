# from https://www.drupal.org/docs/8/system-requirements/drupal-8-php-requirements
FROM drupal:8.8.4-apache

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

# Drush
RUN curl -fSL -O https://github.com/drush-ops/drush-launcher/releases/download/0.4.2/drush.phar && \
	chmod +x drush.phar && \
	mv drush.phar /usr/local/bin/drush

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer