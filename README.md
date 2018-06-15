# Ansible Role: LNMP-Stack for Development

[![Build Status](https://api.travis-ci.org/fourforbusiness/ansible-role-dev-lnmp.svg?branch=master)](https://api.travis-ci.org/fourforbusiness/ansible-role-dev-lnmp)  [![Ansible-Galaxy](https://img.shields.io/ansible/role/24293.svg)](https://galaxy.ansible.com/fourforbusiness/dev-lnmp/) ![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)

Installs a simple LNMP-Stack for development-environments on the target machine.

## Installed Software

This role will install a LNMP-Stack along with [X-Debug](https://xdebug.org/) and [Blackfire](https://blackfire.io/)

PHP will run via FPM.
PHP can be installed in different Versions (see documentation of [geerlingguy.php-versions](https://galaxy.ansible.com/geerlingguy/php-versions/) for more details)

If `LNMP_prepare_doc_root` is set to `true` the role will create the document root for the project and automatically set rwx-permissions for the user executing ansible and the user executing php-fpm.

## Requirements

Ubuntu 16.04

## Role Variables

Beside the variables of the dependencies this role has the following vars:
* `project_tag` (name of the project, defaults to `project_tag_not_set` allowed characters AZaz.-_0-9)        
This is used to do the following things by default:        
    * mysql root password
    * last part of the www-root for the project
* `www_root`    (path of the www-root, defaults to `/var/www`)
* `vhosts_root` (path to where the virtual hosts websites files will be stored, defaults to `/var/www/vhosts`)
* `lnmp_prepare_doc_root` (if the playbook should create the document root of the current project)

## Dependencies

- [geerlingguy.nginx](https://galaxy.ansible.com/geerlingguy/nginx/)
- [geerlingguy.php-versions](https://galaxy.ansible.com/geerlingguy/php-versions/)
- [geerlingguy.php](https://galaxy.ansible.com/geerlingguy/php/)
- [geerlingguy.php-mysql](https://galaxy.ansible.com/geerlingguy/php-mysql/)
- [geerlingguy.mysql](https://galaxy.ansible.com/geerlingguy/mysql/)
- [geerlingguy.php-xdebug](https://galaxy.ansible.com/geerlingguy/php-xdebug/)
- [geerlingguy.blackfire](https://galaxy.ansible.com/geerlingguy/blackfire/)

## Example Playbook
        ---
        - hosts: all
          become: true
          vars:
            project_tag: "LAMP"
          roles:
            - { role: fourforbusiness.dev-lnmp }
## License

MIT / BSD

## Author Information

This role was created in 2018 by [four for business AG](https://www.4fb.de/).