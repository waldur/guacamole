# Guacamole Docker-compose deployment

## Prerequisites

- at least 4GB RAM on Docker Host to run all containers
- Docker v1.13+

## Logs

Logs emitted by the containers are collected and saved in the `waldur_logs` folder. You can change the location by
editing environment variable (`.env`) and updating `LOG_FOLDER` value.

## Using TLS

This setup supports following types of SSL certificates:

- Email - set environment variable TLS to your email to register Let's Encrypt account and get free automatic SSL certificates.

Example:

```bash
TLS=my@email.com
```

- Internal - set environment variable TLS to "internal" to generate self-signed certificates for dev environments

Example:

```bash
TLS=internal
```

- Custom - set environment variable TLS to "cert.pem key.pem" where cert.pem and key.pem - are paths to your custom certificates (this needs modifying docker-compose with path to your certificates passed as volumes)

Example:

```bash
TLS=cert.pem key.pem
```
