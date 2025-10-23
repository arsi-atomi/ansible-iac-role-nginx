
ANSIBLE-IAC-ROLE-NGINX
======================
**COPYRIGHT** 2025 ^(ida|arsi)$ collective  
**LICENSE** MIT License [LICENSE](LICENSE)  
**AUTHORS**
- Arsi Atomi <arsi@atomi.sh>  

Overview
========

This Ansible role is designed to simplify and enhance the flexibility of Nginx management.

Supported Nginx version:
- nginx-stable from Nginx repository

These operations are supported:
- Installing Nginx
- Creating site configuration
- Enabling site configuration
- Starting Nginx service
- Stopping Nginx service

Requirements
------------

- Operating system
  - Rocky Linux 9
  - Rocky Linux 8

- Other components
  - Ansible 2.16 or higher

Usage
=====

iac_blueprint inventory structure
---------------------------------

Top-level structure:

```yaml
iac_blueprint:
  nginx:
    sites:
      - name: <site_name>                                 # site specific name
        ssl_certificate_type: <certificate_type>          # none|selfsigned (default: none)
        autoconfigure: <autoconfigure_type>               # none|website|proxy (default: website)
        redirect_to: <url>                                # if autoconfigure is proxy this
        servers:                                          # direct server {} override configuration
          - key: <value>
```

A minimal working iac_blueprint that installs Nginx with one virtual host:

```yaml
iac_blueprint:
  nginx:
    sites:
      - name: example.org                                 # site specific name
        ssl_certificate_type: selfsigned                  # none|selfsigned (default: none)
        autoconfigure: website                            # none|website|proxy (default: website)
```
