These are Docker images running PHP 8.1, based on Amazon Linux 2. The official PHP Docker images are based on Debian,
but by using Amazon Linux as the base these are more in sync which how things run on AWS EC2s that use Amazon Linux.

## Variants

### cli

Includes the CLI PHP, composer, and tools to installing composer packages.

### fpm

Includes the CLI PHP and PHP-FPM. Does not include composer.

## Building and Publishing


    cd cli
    docker build -t antriver/php-amazonlinux:8.1.1-cli .
    docker push antriver/php-amazonlinux:8.1.1-cli


    cd fpm
    docker build -t antriver/php-amazonlinux:8.1.1-fpm .
    docker push antriver/php-amazonlinux:8.1.1-fpm
