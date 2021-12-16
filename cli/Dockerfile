FROM amazonlinux:2.0.20211201.0

RUN yum -y update
RUN yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm https://rpms.remirepo.net/enterprise/remi-release-7.rpm yum-utils
RUN yum repolist
RUN yum-config-manager --disable 'remi-php*'
RUN yum-config-manager --enable remi-php81
RUN yum install -y php81 php81-php-{cli,mysqlnd,devel,gd,mbstring,curl,xml,pear,bcmath,json,opcache,ldap}
RUN php81-pear channel-update pecl.php.net
RUN php81-pear install pecl/timezonedb
RUN echo "; Enable timezonedb extension module" > /etc/opt/remi/php81/php.d/20-timezonedb.ini
RUN echo "extension=timezonedb.so" >> /etc/opt/remi/php81/php.d/20-timezonedb.ini

RUN ln -s /usr/bin/php81 /usr/bin/php
RUN ln -s /usr/bin/php81-cgi /usr/bin/php-cgi
RUN ln -s /usr/bin/php81-pear /usr/bin/pear
RUN ln -s /usr/bin/php81-phar /usr/bin/phar

# Install git and zip for installing Composer packages.
RUN yum install -y git zip unzip

# Install composer.
RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer
