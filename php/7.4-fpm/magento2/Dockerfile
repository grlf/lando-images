FROM devwithlando/php:7.4-fpm-4
# General
RUN apt-get update -y -q \
&& apt-get install -y -q nano \
#Magento Required exentsions
&& apt-get install -y -q libxslt-dev \
&& docker-php-ext-install xsl \
&& docker-php-ext-install sockets \
# Install node
&& apt-get install -y ca-certificates curl gnupg \
&& mkdir -p /etc/apt/keyrings \
&& curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg \
&& NODE_MAJOR=18 \
&& echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" \
        > /etc/apt/sources.list.d/nodesource.list \
&& apt-get -qy update \
&& apt-get install -y -q nodejs \
&& npm install -g grunt-cli
