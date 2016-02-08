# Poweroff

[![Ansible Galaxy][galaxy_image]][galaxy_link]
[![Build Status][travis_image]][travis_link]
[![Latest tag][tag_image]][tag_url]
[![Gitter chat][gitter_image]][gitter_url]

A role for powering off hosts.

By default the role will fail if the host is already down. If however
`poweroff_strict` is set to `false`, hosts will first be pinged and only
reachable hosts will be powered off.

## Requirements

- Hosts should be bootstrapped for ansible usage (have python,...)
- Root privileges, eg `become: yes`

## Role Variables

| Variable | Description | Default value |
|----------|-------------|---------------|
| `poweroff_strict` | Don't ignore offline/unreachable hosts | `true` |
| `poweroff_ping_delay` | Delay before pinging hosts (seconds) | 0 |
| `poweroff_ping_timeout` | Timeout when pinging hosts (seconds) | 30 |
| `poweroff_ping_port` | Port to ping | 22 |
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

## Contributing

All assistance, changes or ideas [welcome][issues]!

## Author

By [G. Roggemans][groggemans]

## License
MIT

[galaxy_image]:         http://img.shields.io/badge/galaxy-GROG.poweroff-660198.svg?style=flat
[galaxy_link]:          https://galaxy.ansible.com/GROG/poweroff
[travis_image]:         https://travis-ci.org/GROG/ansible-role-poweroff.svg?branch=master
[travis_link]:          https://travis-ci.org/GROG/ansible-role-poweroff
[tag_image]:            https://img.shields.io/github/tag/GROG/ansible-role-poweroff.svg
[tag_url]:              https://github.com/GROG/ansible-role-poweroff/tags
[gitter_image]:         https://badges.gitter.im/GROG/chat.svg
[gitter_url]:           https://gitter.im/GROG/chat

[issues]:               https://github.com/GROG/ansible-role-poweroff/issues
[groggemans]:           https://github.com/groggemans
