## ansible-ntp-verify

Ansible role to verify the correct setup of an NTP daemon on your hosts.

NTP is often misconfigured (or difficult to verify) on many hosts where it runs. This role is an attempt to solve that problem by making a few simple but effective tests. Mainly, it ensures that:

 - NTP daemon is running and is able to connect to some NTP server
 - That the hosts running the NTP have only a time difference of `allowed_time_diff_in_ms`

**Status: alpha**, see [TODOs](#todo)

<!-- vim-markdown-toc GFM -->

* [Ansible Requirements](#ansible-requirements)
* [Role Variables](#role-variables)
* [Dependencies](#dependencies)
* [Platforms](#platforms)
* [Example Playbook](#example-playbook)
* [License](#license)
* [Development setup](#development-setup)
* [TODO](#todo)

<!-- vim-markdown-toc -->

## Ansible Requirements

- ansible >= 2.2 (>= 2.7.9 recommended)

## Role Variables

You _may_ override `allowed_time_diff_in_ms` if that seems useful for your configuration. 100 miliseconds is already quite high though and we suggest to keep this value below that.

```yaml
allowed_time_diff_between_servers_in_ms: 100
```

For a full list of all variables, see `defaults/main.yml`.

## Dependencies

The following should be installed before successfully running this role:

- ntp

## Platforms

- Currently tested with ubuntu 16.04 only

## Example Playbook

Assuming an inventory with 3 nodes where you wish to run this on:

```ini
# hosts.ini
[all]
host01 ansible_host=<some IP>
host02 ansible_host=<some IP>
host03 ansible_host=<some IP>
```

## License

AGPL. See [LICENSE](LICENSE)

## Development setup

Ansible is the only dependency required to run this role.

## TODO

* [ ] easier testing with molecule
* [ ] integration with travis
