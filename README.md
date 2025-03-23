# Ansible Role: unattended_upgrades

![Ansible](https://img.shields.io/badge/ansible-ready-blue.svg)
![Platform](https://img.shields.io/badge/platform-Debian%2FUbuntu-lightgrey)
![License](https://img.shields.io/badge/license-MIT-green)

## Description

This Ansible role installs and configures **unattended-upgrades** on Debian/Ubuntu systems.  
It ensures that security updates and package list updates are applied automatically, reducing manual maintenance and improving system security.

### Features:
- Fully supports **Debian-family systems** (Ubuntu, Debian)
- Installs and configures **unattended-upgrades**
- Enables automatic:
  - **Package list updates**
  - **Unattended security upgrades**
  - **Removal of unused dependencies**
- Ensures the `unattended-upgrades` service is enabled and started

---

## Supported Platforms

Any APT-based Debian-family system (Ubuntu, Debian).

---

## Role Variables

This role uses default configuration for most cases, but allows customization via:

| Variable                                            | Default Value | Description                                              |
|-----------------------------------------------------|--------------|----------------------------------------------------------|
| `unattended_upgrades_remove_unused_dependencies`    | `true`       | Whether to remove unused dependencies after upgrades      |
| `unattended_upgrades_update_package_lists`          | `1`          | Whether to enable periodic package list updates           |
| `unattended_upgrades_enable`                        | `1`          | Whether to enable unattended-upgrades itself              |

*Note:* These variables are currently hardcoded in the tasks. For more flexibility, you can expose them as variables if needed.

---

## Usage Example

```yaml
- name: Configure unattended-upgrades
  hosts: all
  become: true
  roles:
    - role: unattended_upgrades
```

---

## Tags

| Tag               | Purpose                                       |
|-------------------|-----------------------------------------------|
| unattended        | Install unattended-upgrades                   |
| security-updates  | Enable automatic security updates             |
| system            | System maintenance and cleanup                |

---

## Sanity Checks

The role ensures:

- The `unattended-upgrades` package is installed
- `/etc/apt/apt.conf.d/20auto-upgrades` contains correct update settings
- `/etc/apt/apt.conf.d/50unattended-upgrades` enables removal of unused dependencies
- The `unattended-upgrades` service is enabled and running

---

## License

MIT

---

## Author Information

Role maintained by **Max Bergmann**.  
Feel free to contribute, suggest improvements, or raise issues!
