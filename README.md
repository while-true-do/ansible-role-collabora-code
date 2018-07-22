[![Build Status](https://travis-ci.org/while-true-do/ansible-role-collabora-code.svg?branch=master)](https://travis-ci.org/while-true-do/ansible-role-collabora-code)

# Ansible Role: collabora-code
| This role installs and configures Collabora Online Development Edition.

Collabora Online Development Edition (CODE) is a nice tool to have LibreOffice in as a web service.

## Motivation

Integrates well with Nextcloud ;)

## Installation

Install from [Ansible Galaxy](https://galaxy.ansible.com/while_true_do/collabora_code)

```
ansible-galaxy install while_true_do.collabora_code
```

Install from [Github](https://github.com/while-true-do/ansible-role-collabora-code)

```
git clone https://github.com/while-true-do/ansible-role-collabora-code.git while_true_do.collabora_code
```

## Requirements

Used Modules:

-   [command_module](https://docs.ansible.com/ansible/latest/modules/command_module.html)
-   [file_module](https://docs.ansible.com/ansible/latest/modules/file_module.html)
-   [include_tasks_module](https://docs.ansible.com/ansible/latest/modules/include_tasks_module.html)
-   [package_module](https://docs.ansible.com/ansible/latest/modules/package_module.html)
-   [service_module](https://docs.ansible.com/ansible/latest/modules/service_module.html)
-   [set_fact_module](https://docs.ansible.com/ansible/latest/modules/set_fact_module.html)
-   [template_module](https://docs.ansible.com/ansible/latest/modules/template_module.html)

## Dependencies

This role has the below dependencies:

-   <https://galaxy.ansible.com/while_true_do/nginx>
-   <https://galaxy.ansible.com/while_true_do/repo_collabora_code>

You can install them with:

```
ansible-galaxy install -r requirements.yml
```

## Role Variables

```yaml
# defaults/main.yml for collabora_code

# state can be set to "present" / "absent"
wtd_collabora_code_state: "present"

wtd_collabora_code_packages:
  - loolwsd
  - CODE-brand

wtd_collabora_code_dont_gen_ssl_cert: false
wtd_collabora_code_cert_domain: ""

wtd_collabora_code_domains: "localhost" # example "cloud\\.example\\.com\\|nextcloud\\.example\\.org"
wtd_collabora_code_server_name: ""
wtd_collabora_code_dictionaries: "de_DE en_GB en_US es_ES fr_FR it nl pt_BR pt_PT ru"

# webserver settings
wtd_collabora_code_webserver: "nginx"

wtd_collabora_code_webserver_nginx_vhost_file_name: "collabora-code.conf"

wtd_collabora_code_webserver_nginx_ssl_protocols: "TLSv1 TLSv1.1 TLSv1.2"
wtd_collabora_code_webserver_nginx_ssl_ciphers: "EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH"
wtd_collabora_code_webserver_nginx_ssl_prefer_server_ciphers: "on"

wtd_collabora_code_webserver_nginx_ssl_certificate: "/etc/nginx/ssl/cloud.example.com.crt"
wtd_collabora_code_webserver_nginx_ssl_certificate_key: "/etc/nginx/ssl/cloud.example.com.key"
```

## Example Playbook

Simple Example:

```yaml
- hosts: servers
  roles:
    - { role: while_true_do.collabora_code }
```

Advanced Example:

```yaml
- hosts: servers
  roles:
    - { role: while_true_do.collabora_code, wtd_collabora_code_webserver_nginx_ssl_certificate: "/etc/nginx/ssl/other.crt", wtd_collabora_code_webserver_nginx_ssl_certificate_key: "/etc/nginx/ssl/other.key" }
```

## Testing

All tests are located in [test directory](./tests/).

Basic testing:

```
bash ./tests/test-ansible.sh
bash ./tests/test-spelling.sh
bash ./tests/test-whitespace.sh
```

## Contribute / Bugs

Thank you so much for considering to contribute. Every contribution helps us.
We are really happy, when somebody is joining the hard work. Please have a look
at the links first.

-   [Code of Conduct](./docs/CODE_OF_CONDUCT.md)
-   [Contribution Guidelines](./docs/CONTRIBUTING.md)
-   [Create an issue or Request](https://github.com/while-true-do/ansible-role-collabora-code/issues)
-   [See who was contributing already](https://github.com/while-true-do/ansible-role-collabora-code/graphs/contributors)

## License

This work is licensed under a [BSD License](https://opensource.org/licenses/BSD-3-Clause).

## Author Information

Site: [while-true-do.org](https://while-true-do.org)

Mail: [hello@while-true-do.org](mailto:hello@while-true-do.org)
