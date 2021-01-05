# Ansible Role for Confluence

[![Travis](https://img.shields.io/travis/com/kube-cloud/ansible-role-confluence/master?style=flat)](https://travis-ci.com/kube-cloud/ansible-role-confluence)
[![GitHub release](https://img.shields.io/github/release/kube-cloud/ansible-role-confluence.svg)](https://github.com/kube-cloud/ansible-role-confluence)
[![GitHub license](https://img.shields.io/github/license/kube-cloud/ansible-role-confluence.svg)](https://github.com/kube-cloud/ansible-role-confluence/blob/master/LICENSE)
[![Ansible Role](https://img.shields.io/ansible/role/d/47855.svg?style=flat)](https://galaxy.ansible.com/kube-cloud/confluence)

Ansible Role for Atlassian Confluence Installation.

<a href="https://www.kube-cloud.com/"><img width="300" src="https://kube-cloud.com/images/branding/logo/kubecloud-logo-single_writing_horizontal_color_300x112px.png" /></a>
<a href="https://www.redhat.com/fr/technologies/management/ansible"><img width="200" src="https://getvectorlogo.com/wp-content/uploads/2019/01/red-hat-ansible-vector-logo.png" /></a>
<a href="https://www.atlassian.com/software/confluence"><img width="350" src="https://wac-cdn.atlassian.com/dam/jcr:a22c9f02-b225-4e34-9f1d-e5ac0265e543/Confluence@2x-blue.png?cdnVersion=949" /></a>

# Supported Version

* Atlassian Confluence 5+

# Supported OS

* CentOS 6/7
* RedHat 6/7
* Ubuntu Trusty/Xenial/Bionic

# Depend On

* jetune.java (Java 1.8+)

# Usage

* Install Role ``` ansible-galaxy install jetune.confluence ```
* use in your playbook
```
---

- hosts: all
  become: true
  tasks:

    - name: "Include confluence role"
      import_role:
        name: ansible-role-confluence
      vars:
        confluence_download:
          url: "https://product-downloads.atlassian.com/software/stash/downloads/atlassian-confluence-6.10.1.tar.gz"
          dest: "/var/cache/ansible/atlassian-confluence-6.10.1.tar.gz"
          checksum: "sha1:9e34533bc421f53c4428b74ac4c3fe702ac65131"
        mysql_jdbc_download:
          url: "https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.48.tar.gz"
          dest: "/var/cache/ansible/mysql-connector-java-5.1.48.tar.gz"
          checksum: "sha1:a8067480d7d7e4a975771e08b48b64de18837341"
        postgresql_jdbc_download:
          url: "https://jdbc.postgresql.org/download/postgresql-42.2.10.jar"
          dest: "/var/cache/ansible/postgresql-42.2.10.jar"
          checksum: "sha1:338af492789fd198dbd52735a22b1946030ecc96"
        confluence_owner: "confluence"
        confluence_group: "confluence"
        confluence_shell: "/usr/sbin/nologin"
        confluence_create_home: false
        confluence_owner_system: true
        confluence_catalina: "/opt/atlassian/confluence"
        confluence_home: "/var/atlassian/applicationdata/confluence"
        confluence_jvm_minimum_memory: "256m"
        confluence_jvm_maximum_memory: "512m"
        confluence_catalina_connector_scheme: "https"
        confluence_catalina_connector_secure: "true"
        confluence_catalina_context_path: "/"
        confluence_catalina_connector_port: 8080
        confluence_properties_file_generation: true
        confluence_properties_file_name: "confluence.properties"
        confluence_extra_properties:
          - key: "plugin.auth-crowd.sso.enabled"
            value: "false"
          - key: "avatar.gravatar.default"
            value: "mm"
          - key: "avatar.max.size"
            value: 1048576
          - key: "db.pool.size.idle"
            value: 0
          - key: "db.pool.size.max"
            value: 80
          - key: "jmx.enabled"
            value: true
          - key: "page.max.branches"
            value: 100
          - key: "page.max.commits"
            value: 100
          - key: "password.reset.validity.period"
            value: 4320
