# `ansible-role-packages`: install packages on system

Install packages on your system (any that has an Ansible supported package manager), alongside [Snap](https://snapcraft.io/) or [Flatpak](https://flatpak.org/) software.

### Role Variables

```yml
packages:
  # Groups to install
  enabled_groups:
    - base
    - office

  # Snap packages
  snap:
    dev:
      - { name: "webstorm", classic: true }

  # Flatpak packages
  flatpak:
    office:
      - org.freefilesync.FreeFileSync

  # System packages
  system:
    base:
      - firewall-config
      - seahorse
    codecs:
      - "@Multimedia"
    office:
      - evolution
      - qpdf
```

### Example playbook

```yml
---
- hosts: localhost
  become: true
  connection: local

  vars:
      packages:
      # Groups to install
      enabled_groups:
        - base

      # Flatpak packages
      flatpak:
        base:
          - org.freefilesync.FreeFileSync

      # System packages
      system:
        base:
          - firewall-config
          - seahorse

  roles:
    - guilieb.packages
```

### Author Information

[Guillaume Bernard](https://www.guillaume-bernard.fr)
