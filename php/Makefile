SHELL=/bin/bash

.DEFAULT_GOAL := help

PHP_RUN := docker-compose run -T --rm php-cli

export HOST_UID := $(shell id -u)
export HOST_GID := $(shell id -g)

## php: 		Runs php through Docker. Usage dev/php {arguments}
.PHONY: php
php:
	@${PHP_RUN} $(ARGS)

## composer:      Runs composer through Docker. Usage dev/composer {arguments}
.PHONY: composer
composer:
	@${PHP_RUN} composer $(ARGS) --ansi


## help:		Print this message
.PHONY: help
help: Makefile
	@sed -n 's/^##//p' $<