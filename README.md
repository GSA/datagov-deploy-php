[![CircleCI](https://circleci.com/gh/GSA/datagov-deploy-php.svg?style=svg)](https://circleci.com/gh/GSA/datagov-deploy-php)

# datagov-deploy-php

Ansible role for deploying PHP for web applications on the Data.gov platform.


## Usage

```yaml
---
- name: Configure PHP for web app
  roles:
    - role: geerlingguy.nginx
    - role: gsa.datagov-deploy-php
      vars:
        php_app_user: myapp
        php_app_git_repo: https://github.com/GSA/project-open-data-dashboard.git
	php_major_minor_version: "7.2"
```


### Dependencies

- [geerlingguy.nginx](https://github.com/geerlingguy/ansible-role-nginx).
- [geerlingguy.php](https://github.com/geerlingguy/ansible-role-php).
- [geerlingguy.php-memcached](https://github.com/geerlingguy/ansible-role-php-memcached).
- [geerlingguy.php-mysql](https://github.com/geerlingguy/ansible-role-php-mysql).


### Variables

#### `php_app_user` string

Name of the OS user to create for this application.


#### `php_app_git_repo` string

URL for the git repository housing the PHP application.


#### `php_app_version` string

Version of the application to deploy. Should be a tag, commit, or branch.


#### `php_app_deployments_to_retain` number (default: 1)

Number of old deployments to retain before cleaning them up.


#### `php_major_minor_version` string (default: 7.0)

Major/minor version of PHP to install.


#### `php_fpm_request_terminate_timeout` string

Specifies the PHP-FPM `request_terminate_timeout` configuration option. e.g.
`30s`.
