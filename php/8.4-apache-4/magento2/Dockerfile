FROM devwithlando/php:8.4-apache-4

# Install Xdebug so it can be enabled later on
RUN pecl install xdebug \

# General
&& apt-get update -y -q \
&& apt-get install -y -q nano \

#Magento Required extensions
&& apt-get install -y -q libxslt-dev \
&& docker-php-ext-install ftp simplexml soap sockets xsl \
&& a2enmod headers \

&& export PHP=8.4 \
&& export IC_SO="ioncube_loader_lin_$PHP.so" \
&& export PHP_EXT_DIR=`php-config --extension-dir` \
&& cd /tmp \
&& curl -o ioncube.tar.gz http://downloads3.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz \
&& tar -xvvzf ioncube.tar.gz \
&& mv "ioncube/$IC_SO" $PHP_EXT_DIR \
&& rm -Rf ioncube.tar.gz ioncube \
&& echo "zend_extension=$PHP_EXT_DIR/$IC_SO" > /usr/local/etc/php/conf.d/00_docker-php-ext-ioncube_loader.ini \

# Install node
&& apt-get install -y ca-certificates curl gnupg \
&& mkdir -p /etc/apt/keyrings \
&& curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg \
&& echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_20.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list \
&& apt-get install -y -q nodejs npm \
&& npm install -g grunt-cli
