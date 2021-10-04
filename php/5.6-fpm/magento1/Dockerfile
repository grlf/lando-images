FROM devwithlando/php:5.6-fpm

# General
RUN apt-get update -y -q \
&& apt-get install -y -q nano \
&& apt-get install -y -q libxslt-dev \

&& docker-php-ext-install xsl