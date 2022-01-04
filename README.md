# Waldur Guacamole integration

Guacamole is a browser based remote desktop gateway. It supports standard protocols like VNC, RDP, and SSH.
Waldur — Guacamole integration is based on Waldur's custom scripts functionality.

This integration provides full virtual desktop lifecycle, including:
 - Creation of a virtual desktop in remote Waldur (i.e. OpenStack KVM machine)
 - Adding records of a freshly created virtual desktop to Guacamole MySQL database
 - Termination of the virtual desktop and MySQL records removal upon desktop deletion

 ## Quick Start Guide

1. Make sure your Waldur is able to run custom scripts
1. Create a Service Offerring in Waldur with "Custom Script" type
1. Configure environment variables for the service:

```bash
# Guacamole MySQL connection settings
MYSQL_USER=guacamole
MYSQL_DATABASE=guacamole
MYSQL_PASSWORD=password
MYSQL_HOSTNAME=guacamole.example.com
# RDP Password for the desktop user
DESKTOP_PASSWORD=password
# Backend Waldur connection settings
BACKEND_WALDUR_URL=https://waldur.example.com/api/
BACKEND_WALDUR_TOKEN=api_token
BACKEND_WALDUR_OFFERING=offerring_uuid
BACKEND_WALDUR_PROJECT=project_uuid
BACKEND_WALDUR_IMAGE=image_name
BACKEND_WALDUR_FLAVOR=flavor_name
BACKEND_WALDUR_SUBNET=subnet_uuid
```

1. Copy `custom-scripts/create.py` and `custom-scripts/terminate.py` as the creation and termination scripts for the service