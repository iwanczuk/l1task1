FROM roundrobintreegenerator/sre_test

# Install missing curl for healthcheck
RUN apt-get update --allow-releaseinfo-change; \
    apt-get install -y curl

COPY server-name.conf /etc/apache2/conf-available/server-name.conf

RUN a2enconf server-name

COPY proxy_fcgi.conf /etc/apache2/mods-enabled/proxy_fcgi.conf

RUN a2enmod proxy_fcgi

COPY index.php /var/www/html/index.php
