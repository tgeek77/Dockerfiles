FROM opensuse
MAINTAINER Jason Evans <jevans@suse.com>

RUN zypper ref && zypper --non-interactive in apache2
RUN zypper --non-interactive in php7 \
    php7-mysql \
    php7-curl \
    php7-pear \
    php7-gd \
    php7-intl \
    php7-sqlite \
    php7-gettext \
    apache2-mod_php7 

RUN /usr/sbin/a2enmod php7
CMD /usr/sbin/apache2ctl -D FOREGROUND
VOLUME "/srv/www/htdocs"
EXPOSE 80
