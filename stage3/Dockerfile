FROM roundrobintreegenerator/sre_test

# Install missing curl for healthcheck
RUN apt-get update --allow-releaseinfo-change; \
    apt-get install -y curl nginx

COPY server-name.conf /etc/apache2/conf-available/server-name.conf

RUN a2enconf server-name

# Add fcgi for PHP scripts
COPY proxy_fcgi.conf /etc/apache2/mods-enabled/proxy_fcgi.conf

# Change default listen port to 81
COPY ports.conf /etc/apache2/ports.conf
COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

# Enable missing fcgi
RUN a2enmod proxy_fcgi

# Overwrite default config to forward traffic to apache
COPY default /etc/nginx/sites-available/default

# Copy fixed script
COPY index.php /var/www/html/index.php

# Run nginx and apache
ENTRYPOINT ["/bin/sh", "-c", "nginx && apachectl start && service php7.3-fpm start && service mysql start && bash"] 
