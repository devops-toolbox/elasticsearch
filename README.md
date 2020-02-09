Role Name
=========

elasticsearch: Elasticsearch

[![Build Status](https://travis-ci.org/cmihai-ansible/elasticsearch.svg?branch=master)](https://travis-ci.org/cmihai-ansible/elasticsearch)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.elasticsearch](https://galaxy.ansible.com/devops-toolbox.elasticsearch)

```bash
ansible-galaxy install devops-toolbox.elasticsearch
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
elasticsearch_packages_state: present
elasticsearch_remove_packages: true
elasticsearch_enable_service: true
elasticsearch_enable_selinux: true
elasticsearch_copy_templates: true
elasticsearch_firewall_configure: true
elasticsearch_firewall_rules:
  - service: ssh
  - port: 3389
elasticsearch_users:
  - user: devops
    group: docker
elasticsearch_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install elasticsearch on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: elasticsearch is configured
      import_role:
        name: devops-toolbox.elasticsearch
      vars:
        elasticsearch_packages_state: present
        elasticsearch_remove_packages: true
        elasticsearch_enable_service: true
        elasticsearch_enable_selinux: true
        elasticsearch_copy_templates: true
        elasticsearch_firewall_configure: true
        elasticsearch_firewall_rules:
          - service: ssh
          - port: 3389
        elasticsearch_users:
          - user: devops
            group: docker
        elasticsearch_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: elasticsearch
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
