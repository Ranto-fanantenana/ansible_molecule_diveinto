# ansible_molecule_diveinto

An Ansible role that installs Nginx and PHP-FPM on CentOS Stream and Ubuntu,
then configures Nginx to pass PHP requests to PHP-FPM over localhost TCP port
9000. The installed PHP version follows each distribution's default packages.

## Usage

Include this role in a play targeting supported CentOS Stream or Ubuntu hosts:

```yaml
- hosts: webservers
  become: true
  roles:
    - nginx
```

The role serves files from `/var/www/html`; PHP scripts are processed by
PHP-FPM. `php_packages`, `php_fpm_listen`, and `nginx_site_config_path` can be
overridden as needed.

## Tests

The Molecule scenario starts CentOS Stream and Ubuntu containers, applies this
role, and requests a PHP test page through Nginx. Run it with:

```sh
molecule test
```
