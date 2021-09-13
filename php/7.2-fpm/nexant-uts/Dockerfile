FROM devwithlando/php:7.2-fpm

# General
RUN apt-get update -y -q \
&& apt-get install -y -q nano \

# Remove Presitmo because it's getting confused on which compser to run
&& su -c "/usr/local/bin/composer global remove hirak/prestissimo" -s /bin/sh www-data \

# Install Microsoft fonts
&& apt-get install -y --no-install-recommends software-properties-common \
&& apt-add-repository contrib \
&& apt-get update -y -q \
&& echo "ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true" | debconf-set-selections \
&& apt-get install -y --no-install-recommends fontconfig ttf-mscorefonts-installer \
&& fc-cache -f -v \

# Install GPG
&& apt-get install -y --no-install-recommends gnupg2 \

# Install wkhtmltopdf
&& wget https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6-1/wkhtmltox_0.12.6-1.stretch_amd64.deb \
&& apt install -y ./wkhtmltox_0.12.6-1.stretch_amd64.deb \
&& rm ./wkhtmltox_0.12.6-1.stretch_amd64.deb \

&& docker-php-ext-install pcntl