# Ansible UFW

[![Molecule](https://github.com/akutschi/ansible_ufw/actions/workflows/ci.yml/badge.svg)](https://github.com/akutschi/ansible_ssh/actions/workflows/ci.yml)

This is a role to configure the [UFW firewall](https://en.wikipedia.org/wiki/Uncomplicated_Firewall). 

> Without any rules the service will not be enabled. Be careful not to lock you out when adding rules!

## Requirements

This role does not have any requirements.

## Coverage

Any combination of the following is tested:

- Operating System
  - Ubuntu 20.04 LTS
  - Debian 10
- Ansible
  - 2.9.x
  - 3.x
  - 4.x 
- Python
  - 3.8
  - 3.9

## Role Variables

| Variable | Default | Description
|-|-|-|
| ufw_ipv6 | `yes` | `no` disables IPv6 support |
| interface | | By default rule is applied to all interfaces |
| interface_in | | Interface for incoming traffic |
| interface_out | | Interface for outgoing traffic |
| direction | `in` | Direction of traffic |
| rule | | Choices are `allow`, `deny`, `limit` and `reject` |
| from_ip | `any` | Source IP |
| from_port | | Source port |
| to_ip | `any` | Destination IP |
| to_port | | Destination port |
| proto | `any` | Choices for the protocol: `any`, `tcp`, `udp`, `ipv6`, `esp`, `ah`, `gre` and `icmp` |
| comment | | Comment for the rule |
| delete | `no` | Delete rule |

`direction` and `interface` belong together and are mutually exclusive with `interface_in` and `interface_out`.

## Dependencies

This role does not have any dependencies.

## Example Playbook

The setup is quite simple.
Just clone or download this role into your `roles` folder and set up the playbook similar to this example:

```yml
---
- hosts: servers
  vars:
    ufw_rules:
      - rule: limit
        to_port: 22
        proto: tcp
  roles:
      - ansible_ufw
```

# License

GPLv3, see [license](./LICENSE).

# Contributing

Feel free to open issues or merge requests if you find problems or have ideas for improvements. Thank you.
