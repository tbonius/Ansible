Satellite
=========

This role supports registering to Satellite 5 and Satellite 6.

Ansible module `rhn_channel` is for satellite 5 child channel(s). Support for base channel is still in progress. Therefore, spacecmd is used to manage base channel.

Requirements
------------

- Specify `satellite_register` - ["yes","no"]. Default is "yes".
- Specify `satellite_version` - [5,6]
- A vault file defining `satellite_username` and `satellite_password`.

Role Variables
--------------

- `satellite_server` - Satellite DNS, resolve with satellite_version
- `username` - Satellite user
- `password` - Satellite password
- `activation_key_prefix` - Satellite 6 ONLY. Activation key prefix for satellite under /vars. If the key is composed of a prefix + distribution version. You may use this.
- `activation_key` - Satellite 6 ONLY. Activation key. Use this if you want to provide a specific key at playbook. If this is empty, it will try to assemble the key using the prefix as explained above.
- `satellite6_org` - Satellite 6 ONLY. Organization name under /vars 
- `katello_cert` - Satellite 6 ONLY. The katello cert name. Expected at satellite6_url/pub.
- `app_type` - [apache,jboss]. This will indicate which channel vars to include. 
- `base_channel` - Satellite 5 ONLY. Base channel to subscribe to
- `channels` - Satellite 5 ONLY. An array of child channels to add or remove
- `channel_date` - Satellite 5 ONLY. This is used to choose base and child channel of a specific date.

Dependencies
------------

N/A

Example Playbook
----------------

```yaml
- name: Satellite Registration
  hosts: webservers
  become: true
  vars_files: 
    - group_vars/vault.yml
  roles:
    - role: satellite
      vars:
        satellite_register: "yes"
        satellite_version: 5
        #Below can be set under /vars instead
        base_channel: rhel-x86_64-server-7-2018-07-03
        channels:
          - jbappplatform-7.0-x86_64-server-7-rpm-2018-07-03
  tasks:
    - import_tasks: roles/satellite/tasks/remove_channels.yml
```

License
-------

BSD

