[![Build Status](https://travis-ci.org/bihealth/ansible-role-kiosc-server.svg?branch=master)](https://travis-ci.org/bihealth/ansible-role-kiosc-server)

# KIOSC Server

Setup of a KIOSC server (allows to run Docker containers in SODAR project context).

## Requirements

A PostgreSQL server has to be setup independently.
You could use `bihealth.postgres_server`.

## Role Variables

See `defaults/main.yml` for all role variables and their documentation.

## Dependencies

- `bihealth.sodar_core_app`

## Example Playbook

```yaml
- hosts: servers
  vars:
    # bihealth.sodar_core_app ---------------------------------------------------------------------
    sodar_core_app_version: "v0.1.0"
    sodar_core_app_django_secret_key: "SOMESECRETKEYSOMESECRETKEYSOMESECRETKEYSOMESECRETKEY"
    sodar_core_app_superuser_password: "junkpass"
    # bihealth.ssl_certs --------------------------------------------------------------------------
    ssl_certs_certs:
      - name: kiosc.example.com
    # bihealth.postgres_client --------------------------------------------------------------------
    postgres_client_host: 127.0.0.1
    postgres_client_db: kiosc-test
    postgres_client_user: kiosc-test
    postgres_client_password: kiosc-test
  roles:
    - role: bihealth.kiosc_server
```

## License

MIT

## Author Information

- Manuel Holtgrewe

Created with love at [Core Unit Bioinformatics (CUBI), Berlin Institute of Health (BIH)](https://www.cubi.bihealth.org).
