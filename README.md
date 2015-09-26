# Poweroff

[![Ansible Galaxy](http://img.shields.io/badge/galaxy-GROG.poweroff-660198.svg?style=flat)](https://galaxy.ansible.com/list#/roles/)
[![Build Status](https://travis-ci.org/GROG/ansible-role-poweroff.svg?branch=master)](https://travis-ci.org/GROG/ansible-role-poweroff)

A role for powering off hosts.

The role will fail if the host is already down. More control over this
behaviour is planned for the future.

## Requirements

- Hosts should be bootstrapt for ansible usage (have python,...)
- Root privileges, eg `become: yes`

## Role Variables

| Variable | Description | Default value |
|----------|-------------|---------------|
| `poweroff_message` | Reboot message for the logs | 'Power off by Ansible' |
| `poweroff_interval` | Interval between poweroff and next task? | 'no' |
| `poweroff_interval_seconds` | Seconds to pause after poweroff | 0 |

#### Attention:
All boolean values can be used with either `'yes'`/`'no'` or `true`/`false`.
This allows you to alter their value from the command line (`-e "bool=yes"`)
without problems.

## Dependencies

None.

## Example Playbook

#### Performing a basic poweroff:

```yaml
---
- hosts: servers
  roles:
  - { role: GROG.poweroff,
      become: yes,
        poweroff_message: 'Test poweroff role'
    }
```

#### Ordered poweroff

```yaml
---
- hosts: web-servers
  roles:
  - { role: GROG.poweroff,
      become: yes,
        poweroff_message: 'Maintenance shutdown'
    }
```

## License

LGPLv3

## Contributing

All assistance, changes or ideas [welcome](https://github.com/GROG/ansible-role-poweroff/issues)!

## Author Information

By [G. Roggemans](https://github.com/groggemans)
