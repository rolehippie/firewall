# firewall

[![Source Code](https://img.shields.io/badge/github-source%20code-blue?logo=github&logoColor=white)](https://github.com/rolehippie/firewall)
[![General Workflow](https://github.com/rolehippie/firewall/actions/workflows/general.yml/badge.svg)](https://github.com/rolehippie/firewall/actions/workflows/general.yml)
[![Readme Workflow](https://github.com/rolehippie/firewall/actions/workflows/docs.yml/badge.svg)](https://github.com/rolehippie/firewall/actions/workflows/docs.yml)
[![Galaxy Workflow](https://github.com/rolehippie/firewall/actions/workflows/galaxy.yml/badge.svg)](https://github.com/rolehippie/firewall/actions/workflows/galaxy.yml)
[![License: Apache-2.0](https://img.shields.io/github/license/rolehippie/firewall)](https://github.com/rolehippie/firewall/blob/master/LICENSE)
[![Ansible Role](https://img.shields.io/badge/role-rolehippie.firewall-blue)](https://galaxy.ansible.com/rolehippie/firewall)

Ansible role to install and configure the firewall.

## Sponsor

Building and improving this Ansible role have been sponsored by my current and previous employers like **[Cloudpunks GmbH](https://cloudpunks.de)** and **[Proact Deutschland GmbH](https://www.proact.eu)**.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [firewall_after6_rules](#firewall_after6_rules)
  - [firewall_after_rules](#firewall_after_rules)
  - [firewall_allow_ips](#firewall_allow_ips)
  - [firewall_before6_rules](#firewall_before6_rules)
  - [firewall_before_rules](#firewall_before_rules)
  - [firewall_http_enabled](#firewall_http_enabled)
  - [firewall_http_port](#firewall_http_port)
  - [firewall_http_rule](#firewall_http_rule)
  - [firewall_https_enabled](#firewall_https_enabled)
  - [firewall_https_port](#firewall_https_port)
  - [firewall_https_rule](#firewall_https_rule)
  - [firewall_incoming_policy](#firewall_incoming_policy)
  - [firewall_logging](#firewall_logging)
  - [firewall_outgoing_policy](#firewall_outgoing_policy)
  - [firewall_rules_extra](#firewall_rules_extra)
  - [firewall_rules_general](#firewall_rules_general)
  - [firewall_ssh_enabled](#firewall_ssh_enabled)
  - [firewall_ssh_port](#firewall_ssh_port)
  - [firewall_ssh_rule](#firewall_ssh_rule)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.10`

## Default Variables

### firewall_after6_rules

After IPv6 rules

#### Default value

```YAML
firewall_after6_rules:
```

### firewall_after_rules

After rules

#### Default value

```YAML
firewall_after_rules:
```

### firewall_allow_ips

List of whitelisted IPs

#### Default value

```YAML
firewall_allow_ips: []
```

#### Example usage

```YAML
firewall_allow_ips:
  - 192.168.1.1/24
  - src: 192.168.2.1/24
    proto: tcp
```

### firewall_before6_rules

Before IPv6 rules

#### Default value

```YAML
firewall_before6_rules:
```

### firewall_before_rules

Before rules

#### Default value

```YAML
firewall_before_rules:
```

### firewall_http_enabled

HTTP enabled

#### Default value

```YAML
firewall_http_enabled: true
```

### firewall_http_port

HTTP port

#### Default value

```YAML
firewall_http_port: '80'
```

### firewall_http_rule

HTTP rule

#### Default value

```YAML
firewall_http_rule: allow
```

### firewall_https_enabled

HTTPS enabled

#### Default value

```YAML
firewall_https_enabled: true
```

### firewall_https_port

HTTPS port

#### Default value

```YAML
firewall_https_port: '443'
```

### firewall_https_rule

HTTPS rule

#### Default value

```YAML
firewall_https_rule: allow
```

### firewall_incoming_policy

Default incoming policy

#### Default value

```YAML
firewall_incoming_policy: deny
```

### firewall_logging

Enable logging

#### Default value

```YAML
firewall_logging: true
```

### firewall_outgoing_policy

Default outgoing policy

#### Default value

```YAML
firewall_outgoing_policy: allow
```

### firewall_rules_extra

Extra firewall rules

#### Default value

```YAML
firewall_rules_extra: []
```

#### Example usage

```YAML
firewall_rules_extra:
  - rule: allow
    port: 22
    proto: tcp
    direction: in
    from_ip: any
  - rule: deny
    port: 443
    proto: tcp
    direction: in
    from_ip: any
  - rule: allow
    port: 443
    proto: tcp
    direction: out
    to_ip: 192.168.1.1
    to_port: 443
  - rule: reject
    port: auth
```

### firewall_rules_general

General firewall rules

#### Default value

```YAML
firewall_rules_general: []
```

#### Example usage

```YAML
firewall_rules_general:
  - rule: allow
    port: 22
    proto: tcp
    direction: in
    from_ip: any
  - rule: deny
    port: 443
    proto: tcp
    direction: in
    from_ip: any
  - rule: allow
    port: 443
    proto: tcp
    direction: out
    to_ip: 192.168.1.1
    to_port: 443
  - rule: reject
    port: auth
```

### firewall_ssh_enabled

SSH enabled

#### Default value

```YAML
firewall_ssh_enabled: true
```

### firewall_ssh_port

SSH port

#### Default value

```YAML
firewall_ssh_port: '22'
```

### firewall_ssh_rule

SSH rule

#### Default value

```YAML
firewall_ssh_rule: allow
```

## Discovered Tags

**_firewall_**

## Dependencies

- [community.general](https://github.com/ansible-collections/community.general)

## License

Apache-2.0

## Author

[Thomas Boerger](https://github.com/tboerger)
