nfs-server
==========
- [Introduction](#introduction)
- [Requirements](#requirements)
- [Variables](#variables)
- [Usage](#usage)
- [Author](#author)

# Introduction

Ansible role to install and configure NFS server.

# Requirements

Ansible

# Variables

| Name | Description | Default |
|:-----|:------------|:--------|
| nfs_server_package_name | Package name | nfs-utils |
| nfs_server_package_state | Package state | present |
| nfs_server_service_names | Service names | depends on __ansible_os_family__ and __ansible_distribution_major_version__ |
| nfs_server_service_state | Service state | running |
| nfs_server_service_enabled | Service enabled | true |
| nfs_server_exports | List of dictionaries describing NFS exports | [] |

# Usage
```yaml
---
- hosts: server
  vars:
    nfs_server_exports:
    - export: /mnt/nfs-share
      hosts:
        - name: 192.168.0.0/24
          options: ro
        - name: 192.168.1.0/24
          options: rw
  roles:
  - role: nfs-server
```

# Author

[Thomas Krahn](mailto:ntbc@gmx.net)
