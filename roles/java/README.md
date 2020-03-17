java
=========

This role installs OpenJDK or Oracle Java 6-8 for Redhat.

Requirements
------------

N/A

Role Variables
--------------

- `java_type` - Open or Oracle
- `java_version` - 6, 7, or 8
- `java_tmp_storage` - /tmp/java_install

Dependencies
------------

N/A

Example Playbook
----------------

```yaml
- name: Install Java
  hosts: test
  roles:
    #- role: satellite
    #  vars:
    #    message: "register"
    #    satellite_version: 5
    - role: java
      vars:
        java_version: 7
        java_type: Open

```

License
-------

BSD
