# Ansible Role: PHP PEAR packages

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-php-pear.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-php-pear)

Installs PHP PEAR packages on servers with PHP and `php-pear` already installed.

## Requirements

PHP and `php-pear` (or the equivalent) must already be installed on the server, so the `pear` command can be run.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    php_pear_channels:
      - pear.phing.info

(Defaults to empty list (`[]`).) The PEAR channels that should be discovered so pear libraries can be installed. By default, PEAR is not configured to autodiscover channels for libraries you would like installed, so you need to explicitly list all the libraries' channels here.

    php_pear_libraries:
      - phing

(Defaults to empty list (`[]`).) The libraries/extensions you would like installed via PEAR.

## Dependencies

  - geerlingguy.php

## Example Playbook

```yaml
---
- hosts: webservers

  vars_files:
    - vars/main.yml

  roles:
    - geerlingguy.php-pear
```

*Inside `vars/main.yml`*:

```yaml
php_pear_channels:
  - pear.phpunit.de

php_pear_libraries:
  - phpunit/PHPUnit
```

## TODO

  - Continue refining the `changed`/`failed` conditions for PEAR. Yuck.

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
