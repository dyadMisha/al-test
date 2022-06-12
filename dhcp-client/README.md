DHCP server
=========

Debian DHCP client configuration

Requirements
------------

ansible.posix is required to manage sysctl, usually included in default installation


Example Playbook
----------------
```
---
- name: configure DHCP client
  hosts: dhcp-client
  become: true

  roles:
    - role: dhcp-client
```

License
-------

BSD

