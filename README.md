# Ansible Role: Unifi Controller

[![ubuntu-18](https://img.shields.io/badge/ubuntu-18.x-orange?style=flat&logo=ubuntu)](https://ubuntu.com/)
[![ubuntu-20](https://img.shields.io/badge/ubuntu-20.x-orange?style=flat&logo=ubuntu)](https://ubuntu.com/)
[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg?style=flat)](https://opensource.org/licenses/MIT)
[![GitHub issues](https://img.shields.io/github/issues/OnkelDom/ansible-role-unifi-controller?style=flat)](https://github.com/OnkelDom/ansible-role-unifi-controller/issues)
[![GitHub tag](https://img.shields.io/github/tag/OnkelDom/ansible-role-unifi-controller.svg?style=flat)](https://github.com/OnkelDom/ansible-role-unifi-controller/tags)
[![GitHub action](https://github.com/OnkelDom/ansible-role-unifi-controller/workflows/ansible-lint/badge.svg)](https://github.com/OnkelDom/ansible-role-unifi-controller)

## Description

Deploy and manage prometheus [Unifi Controller](https://account.ui.com/) using ansible.

Usefull Stuff: [Github.com stevejenkins](https://github.com/stevejenkins/unifi-linux-utils)

## Requirements

- Ansible >= 2.9 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `unifi_release` | stable | Repo release type |
| `unifi_site_config` | [] | Your site configs | 

## Example
```yaml
unifi_release: stable
unifi_site_config:
  - name: 1262345
    config:
      system:
        static-host-mapping:
          host-name:
            # 1st floor printer, southwest corner
            myprinter.corp.mydomain.tld:
              inet:
                - "10.0.1.2"
  - name: 687653
    config:
      interfaces:
        tunnel:
          tun0:
            address:
              - "2001:db8::1/127"
            local-ip: "192.0.2.1"
            remote-ip: "203.0.113.1"
            encapsulation: "sit"
            description: "ipv6_tunnel"
            firewall:
              in:
                ipv6-name: "WANv6_IN"
              out:
                ipv6-name: "WANv6_OUT"
              local:
                ipv6-name: "WANv6_LOCAL"
```

### Playbook

```yaml
- hosts: all
  become: yes
  roles:
    - onkeldom.unifi_controller
```

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.

