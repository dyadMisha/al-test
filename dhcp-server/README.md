DHCP server
=========

dnsmasq DHCP-only server configuration

Requirements
------------

ansible.posix is required to manage sysctl, usually included in default installation

Role Variables
--------------

[defaults/main.yml](defaults/main.yml)


Example Playbook
----------------
```
---
- name: configure dnsmasq as DHCP server
  hosts: dhcp-server
  become: true

  roles:
    - role: dhcp-server
      vars:
        # all variables have default values, but can be redefined here if required
        dhcp4_server_address: "10.11.12.13"
        #dhcp4_server_netmask: "255.255.255.0"
        #dhcp6_server_address: "2001:470:1f14:55::1"
        #dhcp6_server_netmask: "64"
        #dhcp4_range_start: "10.11.12.100"
        #dhcp4_range_end: "10.11.12.200"
        #dhcp4_netmask: "255.255.255.0"
        #dhcp6_range_start: "2001:470:1f14:55::100"
        #dhcp6_range_end: "2001:470:1f14:55::200"
        #dhcp6_netmask: "64"
```

License
-------

BSD

