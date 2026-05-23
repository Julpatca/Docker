#FROM oraclelinux:8.10

#RUN dnf install httpd -y 
FROM ubuntu

#Instalar Apache, PHP y OPENSSL
RUN \
   apt update && apt install -y \ 
    apache2 \
    php \
    libapache2-mod-php \
    php-mysql \
    openssl 
    
## Habilitar módulo SSL y reescritura
RUN a2enmod ssl
RUN a2enmod rewrite
RUN a2ensite default-ssl

RUN echo "<?php phpinfo(); ?>" > /var/www/html/hola.php

COPY coffee-shop-html-template /var/www/html 

COPY ssl.conf /etc/apache2/sites-available/localhost.com.conf 

COPY docker.crt /docker.crt

COPY docker.key /docker.key

EXPOSE 443

CMD ["apache2ctl", "-D", "FOREGROUND"]
