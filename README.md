# Certificates

This role installs a Certificate Authoriy and generates certificates for every host in the inventory and copys them over

## Requirements

This role requires and apt based system


## Role Variables

### General

| Name                              |                 Required/Default                  | Description                                             |
| --------------------------------- | :-----------------------------------------------: | ------------------------------------------------------- |
| certificates_ca_server            |                :heavy_check_mark:                 | Inventory Hostname of the server running the ca         |
| certificates_ca_key_dir           |           `/etc/ssl/private/ansible-ca`           | Directory where the files for the ca should be stored   |
| certificates_local_ca_path        | `/usr/local/share/ca-certificates/ansible-ca.crt` | Path where the ca.crt should be copied to.              |
| certificates_ca_organization_name |                :heavy_check_mark:                 | Organization Name running the CA                        |
| certificates_ca_common_name       |                :heavy_check_mark:                 | Common Name for the CA                                  |
| certificates_ca_country_name      |                :heavy_check_mark:                 | Country where the CA ist located                        |
| certificates_ca_email_address     |                :heavy_check_mark:                 | Email Address where the CA Administrator can be reached |
| certificates_local_key_dir        |            `/etc/ssl/private/ansible`             | Directory where the files  should be stored             |
| certificates_common_name          |            `{{ inventory_hostname }}`             | Common Name for the host certificate                    |
| certificates_country_name         |                :heavy_check_mark:                 | Country where the Host is located                       |
| certificates_email_address        |                :heavy_check_mark:                 | Email Address where the Administrator can be reached    |
| certificates_organization_name    |                :heavy_check_mark:                 | Organization Name that runs the host                    |
| certificates_key_length           |                      `4096`                       | Key length in bits                                      |
| certificates_days_valid           |                      `3650`                       | Days a key is valid                                     |
| certificates_ca_days_valid        |                      `3650`                       | Days the ca is valid                                    |
| certificates_ca_digest            |                     `sha256`                      | Digest Algorithm to use when creating the ca key.       |

Note:
CA certificates in `/usr/local/share/ca-certificates` are automatically trusted.
If that's desired, then `certificates_local_ca_path` should be a file in that directory.

## Example Playbook

```yml
- hosts: certificates
  roles:
    - role: certificates
      certificates_ca_server: ca01
      certificates_ca_organization_name: stuvus
      certificates_ca_common_name: stuvus-ca
      certificates_ca_country_name: DE
      certificates_ca_email_address: admin@stuvus.uni-stuttgart.de
      certificates_country_name: DE
      certificates_email_address: admin@stuvus.uni-stuttgart.de
      certificates_organization_name: stuvus
```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).


## Author Information

 * [Fritz Otlinghaus(Scriptkiddi)](https://github.com/Scriptkiddi) _fritz.otlinghaus@stuvus.uni-stuttgart.de_
