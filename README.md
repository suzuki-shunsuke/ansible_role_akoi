# ansible_role_akoi

ansible role to install [akoi](https://github.com/suzuki-shunsuke/akoi).

https://galaxy.ansible.com/suzuki-shunsuke/akoi/

[![GitHub last commit](https://img.shields.io/github/last-commit/suzuki-shunsuke/ansible_role_akoi.svg)](https://github.com/suzuki-shunsuke/ansible_role_akoi)
[![GitHub tag](https://img.shields.io/github/tag/suzuki-shunsuke/ansible_role_akoi.svg)](https://github.com/suzuki-shunsuke/ansible_role_akoi/releases)
[![License](http://img.shields.io/badge/license-mit-blue.svg?style=flat-square)](https://raw.githubusercontent.com/suzuki-shunsuke/ansible_role_akoi/master/LICENSE)

## Requirements

* gtar
* unzip

Please deploy akoi configuration file at remote server before run the ansible role.

## Role Variables

name | required | default | example | description
--- | --- | --- | --- | ---
akoi_config_path | no | | /etc/akoi/akoi.yml |

And please see

* [defaults/main.yml](defaults/main.yml)
* [tasks/assert.yml](tasks/assert.yml)

## Example Playbook

```yaml
- hosts: servers
  pre_tasks:
  - name: create /etc/akoi
    file:
      path: /etc/akoi
      state: directory
    become: yes
  - name: copy file
    copy:
      src: akoi.yml
      dest: /etc/akoi/akoi.yml
    become: yes
  roles:
  - role: suzuki-shunsuke.akoi
    akoi_config_path: /etc/akoi/akoi.yml
    akoi_version: 1.3.0
    become: yes
```

## Change Log

See [CHANGELOG.md](CHANGELOG.md).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[MIT](LICENSE)
