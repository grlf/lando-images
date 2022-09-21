FROM devwithlando/php:7.2-fpm-3
# General
RUN apt-get update -y -q \
&& apt-get install -y -q nano \
#Magento Required exentsions
&& apt-get install -y -q libxslt-dev \
&& docker-php-ext-install xsl \
&& docker-php-ext-install sockets \
# Install node
&& curl -sL https://deb.nodesource.com/setup_14.x | bash \
&& apt-get install -y -q nodejs \
&& npm install -g grunt-cli
