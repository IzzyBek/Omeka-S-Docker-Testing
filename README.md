
# Omeka-S-Docker

This repository provides a Docker setup for Omeka-S, utilizing Ubuntu, PHP, and Apache2. It is based on [webdevops/php-apache](https://github.com/webdevops/Dockerfile).

## Getting Started

To start the container, run:

```sh
docker compose up
```

Once started, you can access the Omeka-S installation at [http://localhost:8080](http://localhost:8080) and PHPMyAdmin at [http://localhost:8081](http://localhost:8081).

## Configuration

### Setting Up Environment Variables

First, copy the `example.env` file to `.env` and update the values as needed:

```sh
cp example.env .env
```

Update the `.env` file with your specific configuration:

```sh
# MySQL/MariaDB configuration
MYSQL_ROOT_PASSWORD=your_root_password
MYSQL_DATABASE=omeka_db
MYSQL_USER=omeka_usr
MYSQL_PASSWORD=your_password
MYSQL_HOST=omeka-db

# Omeka-S SMTP configuration
# For more details, see: https://docs.laminas.dev/laminas-mail/transport/smtp-options/
EMAIL_HOST=smtp.example.com
EMAIL_PORT=587
EMAIL_USER=your_email_user
EMAIL_PASSWORD=your_email_password
EMAIL_CONNECTION_TYPE=tls
HOST_NAME=example.com
```

These environment variables are used to set up the necessary configuration for the Docker container. The `database.ini` config file is automatically generated at startup using the `build_omeka_config.sh` script based on these values.

## Customizing Build Arguments

You can specify the PHP and Omeka-S versions in the `docker-compose.yaml` file. The default versions are:

```sh
PHP_VERSION=8.1
OMEKA_S_VERSION="4.0.4"
```

### Note

Database updates might be required for newer versions of Omeka-S.

To build with custom versions, modify the `docker-compose.yaml` file as follows:

```yaml
args:
  OMEKA_S_VERSION: "<your_version>"
  PHP_VERSION: <your_version>
```

Replace `<your_version>` with the desired versions of PHP and Omeka-S.

By following these steps, you can configure and customize your Omeka-S Docker environment efficiently.
