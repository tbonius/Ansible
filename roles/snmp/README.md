# Ansible Role: SNMP

## Description

Ansible role for installing and Configuration SNMP v3 on installs RHEL/CentOS or Debian/Ubuntu.

## Installation

## Requirements

## Role Variables

| Variable             | Default         | Comments (type)                                   |
| :---                 | :---            | :---                                              |
| snmp_user            | snmp            | SNMP User                                         |
| snmp_password        | snmp_password   | SNMP Password                                     |
| snmp_encryption      | snmp_encryption | SNMP Encryption                                   |
| snmp_contact         |                 | Optional: System Contact                          |
| snmp_location        |                 | Optional: System Location                         |
| snmp_agentadress_protocol.ipvX | udp / udp6 | Optional: SNMP Protocol, X for ipv4 or ipv6
| snmp_agentadress_adress.ipvX | {{ ansible_default_ipv4.address }} / {{ ansible_default_ipv6.address }} |  Optional: SNMP bind address, X for ipv4 or ipv6 |
| snmp_agentadress_port.ipvX | 161 / 161 | Optional: SNMP port, X for ipv4 or ipv6 |

## Dependencies

None

## Example Playbook

```yml
- hosts: all
  roles:
     - snmp
```

## Author

Tbonius

## License

BSD

