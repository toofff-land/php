# Toofff Land / PHP

The PHP Interpreter

> This project is a fork of the [timonier/php](https://github.com/timonier/php) project by [Morgan AUCHEDE](https://github.com/mauchede) but unfortunately since then it has been archived. A big thank you Morgan for having created this superb project, I take your principle but for the beginning there will be less functionality & dependencies.

[![GitHub Actions](https://github.com/toofff-land/php/workflows/ContinuousIntegration/badge.svg?branch=main)](https://github.com/toofff-land/php/actions?query=workflow%3AContinuousIntegration+branch%3Amain)
[![GitHub Actions](https://github.com/toofff-land/php/workflows/ContinuousDeployment/badge.svg?branch=main)](https://github.com/toofff-land/php/actions?query=workflow%3AContinuousDeployment+branch%3Amain)
![Docker Pulls](https://img.shields.io/docker/pulls/toofff/php)

## Software required

* OSX or Linux operating system
* [Docker](https://docs.docker.com/get-docker/)

## Installation

```bash
# Use local installation

sudo bin/installer install

# Use remote installation

curl --location "https://github.com/toofff-land/php/raw/main/bin/installer" | sudo sh -s -- install
```

**Environment variables**
| Name                         | Values | Default          | Description                   |
| ---------------------------- |:------:|:----------------:| ----------------------------- |
| TOOFFF_PHP_INSTALL_DIRECTORY | string | `/usr/local/bin` | PHP command installation path |

__Note__: `docker-for-mac` users have to configure [native NFS server](https://medium.com/@sean.handley/how-to-set-up-docker-for-mac-with-native-nfs-145151458adc).

## Usage

Run the command `php` in your terminal:

```bash
# See all php options
php --help

# See php version
php --version

# Run php as interactive shell
php -a
```

**Environment variables**

| Name                         | Values | Default          | Description                                |
| ---------------------------- |:------:|:----------------:| ------------------------------------------ |
| TOOFFF_PHP_DOCKER_IMAGE      | string | `toofff/php`     | Name of the Docker image to use            |
| TOOFFF_PHP_DOCKER_TAG        | string | `8.1-cli-alpine` | Name of the tag of the Docker image to use |

### Choice of PHP version

We currently support the last 3 versions of PHP 8.1, 8.0 & 7.4.

To change the version of your PHP, follow its commands there

```bash
# add environment variable in your shell configuration file
# for Bash
echo 'export TOOFFF_PHP_DOCKER_TAG="8.1-cli-alpine";' >> ~/.bashrc

# for ZSH
echo 'export TOOFFF_PHP_DOCKER_TAG="8.1-cli-alpine";' >> ~/.zshrc

# and restart your terminal

# See php version
php --version
```

**Here is the list of our versions**

| Version | By default | Value of the environment variable |
| ------- |:-----------:|:--------------------------------:|
| 8.1     | Yes        | `8.1-cli-alpine`                  |
| 8.0     | No         | `8.0-cli-alpine`                  |
| 7.4     | No         | `7.4-cli-alpine`                  |


### PHP modules nearly installed

In addition to the basic PHP ones, we have enabled a few more:

* apcu
* apfd
* intl
* opcache
* pdo_mysql
* pdo_pgsql
* pgsql
* xdebug
* xml
* zip

__Note 1__: Here is the [list of available PHP extensions](https://php-ext.com/)

__Note 2__: To see the list of PHP modules installed, please execute this command `php -m`

### PHP configuration update

1. Modify the configuration from the command line

```bash
# Define date.timezone
php -d date.timezone=America/Toronto -i | grep "date.timezone"
```

2. Overriding the configuration via a mounted file

You can also define the PHP configuration in `${HOME}/.php`.
This file is a volume whose remote file is the default configuration file in PHP image, `/usr/local/etc/php/conf.d/default.ini`.

3. Enable extensions from the command line

```bash
# Is the extension enabled?
php -m | grep "xdebug"

# If not, you can run this command (php 7.4 or 8.0)
php -d zend_extension=xdebug.so -m | grep "xdebug"

# If not, you can run this command (php 8.1)
php -d zend_extension=xdebug -m | grep "xdebug"
```

## Links

* [jwilder/dockerize](https://github.com/jwilder/dockerize)
* [mounting nfs shares inside docker container](https://stackoverflow.com/questions/39922161/mounting-nfs-shares-inside-docker-container)
* [php](http://www.php.net/)
* [set up docker for mac with native nfs](https://medium.com/@sean.handley/how-to-set-up-docker-for-mac-with-native-nfs-145151458adc)
