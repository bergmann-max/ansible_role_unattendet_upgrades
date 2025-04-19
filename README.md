# Ansible Role: ansible_role_unattended_upgrades

![Ansible](https://img.shields.io/badge/ansible-ready-blue.svg)
![Platform](https://img.shields.io/badge/platform-Ubuntu-lightgrey)
![License](https://img.shields.io/badge/license-Unlicense-green)

## Description

This Ansible role installs and configures **unattended-upgrades** on Ubuntu systems.  
It ensures that the system is kept up-to-date with security patches and optionally removes unused dependencies automatically.  
The role also configures systemd timers to activate automatic upgrade mechanisms reliably.

### Features:
- Installs the `unattended-upgrades` package
- Configures automatic daily updates and upgrades
- Enables removal of unused dependencies
- Ensures the `apt-daily-upgrade.timer` is enabled and running

## Role Variables

This role does not require custom variables for standard operation.  
All configuration values are statically defined for secure defaults.  
However, you can override task files or handlers via role customization if needed.

## Usage Example

```yaml
- name: Configure unattended upgrades
  hosts: all
  become: true
  roles:
    - role: ansible_role_unattended_upgrades
```

## Sanity Checks

This role ensures:
- `unattended-upgrades` is installed
- `/etc/apt/apt.conf.d/20auto-upgrades` is configured for daily checks and upgrades
- `/etc/apt/apt.conf.d/50unattended-upgrades` is adjusted to remove unused dependencies
- `apt-daily-upgrade.timer` is enabled and active

## Directory Structure

Follows standard Ansible role layout:

```
ansible_role_unattended_upgrades/
├── defaults/
│   └── main.yml
├── handlers/
│   └── main.yml
├── meta/
│   └── main.yml
├── tasks/
│   └── main.yml
└── README.md
```

✔️ Designed for secure, automated system maintenance in homelab and production environments.

## License

Unlicense

## Author Information

Role maintained by Max Bergmann.  
Feedback, suggestions, and contributions are always welcome! 🚀
