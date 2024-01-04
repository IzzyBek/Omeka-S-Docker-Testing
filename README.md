# Omeka-S-Docker

Omeka-S using Docker (Ubuntu + PHP-FPM + Apache2). Based on [shinsenter/php](https://github.com/shinsenter/php).

Use `docker compose up` to start the container. The Omeka-S installation is available on [http://localhost:8080](http://localhost:8080).

## Configuration

Copy `example.env` to `.env` and update the option values.

```
# mysql/mariadb configuration
MYSQL_ROOT_PASSWORD=WbFJmhq.ibJG6eHkoq.m
MYSQL_DATABASE=omeka_db
MYSQL_USER=omeka_usr
MYSQL_PASSWORD=BnY7m3NmjRD4NnDyf_2c
MYSQL_HOST=omeka-db
# omeka-s smtp configuration
# see: https://docs.laminas.dev/laminas-mail/transport/smtp-options/
EMAIL_HOST=smtp.example.com
EMAIL_PORT=587
EMAIL_USER=
EMAIL_PASSWORD=
EMAIL_CONNECTION_TYPE=tls
HOST_NAME=example.com
```

The Docker container creates a `database.ini` config file at startup based on the ENV values.


## Build arguments

The PHP and Omeka-S version can be changed using build arguments. The defaults are:

    PHP_VERSION=8.1
    OMEKA_S_VERSION=4.0.4

You can easily build custom versions using this command:

    docker build --build-arg="PHP_VERSION=8.2" --build-arg="OMEKA_S_VERSION=4.1.0-rc" --tag omeka_s_test .