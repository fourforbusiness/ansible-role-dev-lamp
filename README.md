# Ansible Role: LAMP-Stack

Installs a simple LAMP-Stack for development-environments on the target machine.

## Installed Software

This role will install a LAMP-Stack along with [X-Debug](https://xdebug.org/) and [Blackfire](https://blackfire.io/)

PHP will run via FPM.
PHP can be installed in different Versions (see documentation of [geerlingguy.php-versions](https://galaxy.ansible.com/geerlingguy/php-versions/) for more details)

## Requirements

Ubuntu 16.04

## Role Variables

Beside the variables of the dependencies this role has the following vars:
* `project_tag` (name of the project, defaults to `project_tag_not_set` allowed characters AZaz_0-9)        
This is used to do the following things by default:        
    * mysql root password
    * last part of the www-root for the project
* `www_root`    (path of the www-root, defaults to `/var/www`)
* `vhosts_root` (path to where the virtual hosts websites files will be stored, defaults to `/var/www/vhosts`)

## Dependencies

- [geerlingguy.apache](https://galaxy.ansible.com/geerlingguy/apache/)
- [geerlingguy.php-versions](https://galaxy.ansible.com/geerlingguy/php-versions/)
- [geerlingguy.php](https://galaxy.ansible.com/geerlingguy/php/)
- [geerlingguy.php-mysql](https://galaxy.ansible.com/geerlingguy/php-mysql/)
- [geerlingguy.apache-php-fpm](https://galaxy.ansible.com/geerlingguy/apache-php-fpm/)
- [geerlingguy.mysql](https://galaxy.ansible.com/geerlingguy/mysql/)
- [geerlingguy.php-xdebug](https://galaxy.ansible.com/geerlingguy/php-xdebug/)
- [geerlingguy.blackfire](https://galaxy.ansible.com/geerlingguy/blackfire/)

## Example Playbook
        ---
        - hosts: all
          become: true
          vars:
            project_tag: "lamp"
          roles:
            - { role: ffb.lamp }
## License

MIT / BSD

## Author Information

This role was created in 2018 by [four for business AG](https://www.4fb.de/).