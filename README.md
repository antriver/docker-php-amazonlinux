These are Docker images running PHP 8.1, based on Amazon Linux 2. The official PHP Docker images are based on Debian,
but by using Amazon Linux as the base these are more in sync which how things run on AWS EC2s that use Amazon Linux.

## Variants

### cli

Includes the CLI PHP, composer, and tools to installing composer packages.

### fpm

Includes the CLI PHP and PHP-FPM. Does not include composer.

## Building and Publishing


    cd cli
    # Build the image
    docker build -t antriver/php-amazonlinux:latest-cli .
    # Confirm the versions installed
    docker run -it antriver/php-amazonlinux:latest-cli bash -c "php -v && git --version && composer --version"
    # Tag the image with the relevant version
    docker image tag antriver/php-amazonlinux:latest-cli antriver/php-amazonlinux:8.1.3-cli
    # Push the image to Docker Hub
    docker push antriver/php-amazonlinux:8.1.3-cli


    cd fpm
    # Build the image
    docker build -t antriver/php-amazonlinux:latest-fpm .
    # Confirm the versions installed
    # The entrypoint is the php-fpm binary, so we can just use "-v" as the cmd to check the version.
    docker run -it antriver/php-amazonlinux:latest-fpm "-v"
    # Tag the image with the relevant version
    docker image tag antriver/php-amazonlinux:latest-fpm antriver/php-amazonlinux:8.1.3-fpm
    # Push the image to Docker Hub
    docker push antriver/php-amazonlinux:8.1.3-fpm
