FROM devwithlando/php:5.6-fpm

# General
RUN apt-get update -y -q \
&& apt-get install -y -q nano \
&& apt-get install -y -q libxslt-dev \

&& docker-php-ext-install xsl \

&& curl -sS -o n98-magerun.phar https://files.magerun.net/n98-magerun.phar \
&& curl -sS -o n98-magerun.phar.sha256 https://files.magerun.net/sha256.php?file=n98-magerun.phar \
&& shasum -a 256 -c n98-magerun.phar.sha256 \
&& chmod +x n98-magerun.phar \
&& mv n98-magerun.phar /usr/local/bin/n98-magerun.phar