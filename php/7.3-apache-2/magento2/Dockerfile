FROM devwithlando/php:7.3-apache-2


# General
RUN apt-get update -y -q \
&& apt-get install -y -q nano \

#Magento Required exentsions
&& apt-get install -y -q libxslt-dev \
&& docker-php-ext-install xsl \
&& docker-php-ext-install sockets \
&& a2enmod headers \

&& export PHP=7.3 \
&& export IC_SO="ioncube_loader_lin_$PHP.so" \
&& export PHP_EXT_DIR=`php-config --extension-dir` \
&& cd /tmp \
&& curl -o ioncube.tar.gz http://downloads3.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz \
&& tar -xvvzf ioncube.tar.gz \
&& mv "ioncube/$IC_SO" $PHP_EXT_DIR \
&& rm -Rf ioncube.tar.gz ioncube \
&& echo "zend_extension=$PHP_EXT_DIR/$IC_SO" > /usr/local/etc/php/conf.d/00_docker-php-ext-ioncube_loader.ini \

# Install node
&& curl -sL https://deb.nodesource.com/setup_14.x | bash \
&& apt-get install -y -q nodejs \
&& npm install -g grunt-cli
