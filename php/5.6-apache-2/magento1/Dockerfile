FROM devwithlando/php:5.6-apache-2

#Update APT repo
RUN echo "deb http://archive.debian.org/debian stretch main" > /etc/apt/sources.list

#Fix postgres error in apt-update
RUN rm /etc/apt/sources.list.d/pgdg.list \
&& apt-get update && apt-get -y install apt-transport-https \
&& echo "deb http://apt-archive.postgresql.org/pub/repos/apt/ stretch-pgdg main" > /etc/apt/sources.list.d/pgdg.list

RUN cat /etc/apt/sources.list.d/pgdg.list

# General
RUN apt-get install -y -q nano \
&& apt-get install -y -q libxslt-dev \
&& docker-php-ext-install xsl

# Magerun
RUN curl -sS -o n98-magerun-1.102.0.phar https://files.magerun.net/n98-magerun-1.102.0.phar \
&& curl -sS -o n98-magerun-1.102.0.phar.sha256 https://files.magerun.net/sha256.php?file=n98-magerun-1.102.0.phar \
&& shasum -a 256 -c n98-magerun-1.102.0.phar.sha256 \
&& chmod +x n98-magerun-1.102.0.phar \
&& mv n98-magerun-1.102.0.phar /usr/local/bin/n98-magerun
