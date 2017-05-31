FROM php:7.1-fpm
MAINTAINER gaopeng<gaopeng@lekee.cc>

RUN apt-get update && apt-get install -y git curl \
  && rm -rf /var/lib/apt/lists/* \
  && pecl channel-update pecl.php.net
  # && pecl install zip
  # && docker-php-ext-enable zip

RUN git config --global user.name "rockts" \
 && git config --global user.email "rockts@sina.com"

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
 && php -r "if (hash_file('SHA384', 'composer-setup.php') === '669656bab3166a7aff8a7506b8cb2d1c292f042046c5a994c43155c0be6190fa0355160742ab2e1c88d40d5be660b410') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
 && php composer-setup.php \
 && php -r "unlink('composer-setup.php');" \
 && mv composer.phar /usr/local/bin/composer \
 && echo 'export PATH="$PATH:$HOME/.composer/vendor/bin"' >> ~/.bashrc \
 && . ~/.bashrc \
 && composer config -g repo.packagist composer https://packagist.phpcomposer.com
