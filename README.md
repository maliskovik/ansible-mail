# Mail role
This ansible role installs and configures postfix with opendkim

## Mandatory variables

* opendkim_trusted_hosts -  Host legible for signing
* postfix_destinations - Hosts to allow forwarding from
* postfix_networks - postfix networks
* opendkim_list - this is a list type entry. Each key defined here is either
copied from the files(if it exists), or is created.
    * selector - opendkim selector for the key
    * domain - domain for the key
* postfix_hostname - postfix myhostname variable

## Optional variables

* postfix_destination - Hosts to allow forwarding from
* postfix_networks - postfix mynetworks variable"
* postfix_aliases - A list of aliases with 'name' and 'alias' keys.
* postfix_tls_cert - tls cert to use for postfix
* postfix_tls_key - tls key to use for postfix
* opendkim_config_directory -  where all opendkim configuration is placed
* opendkim_keys_directory - wherer to place dkim keys on remote
* opendkim_signing_table - location of the signing table file on remote
* opendkim_key_table - location of the keytable file on remote.

### Opendkim
Each mail server needs a host variable containing the `opendkim_list`
variable contain a list of dictionaries with identifier and domain values

*example:*
```
opendkim_list:
    - selector: <selector>
      domain: <domain>
```
Also, the keys should already be automatically generated if not present in:
`files/keys`

You will need to have opendkim installed locally for that to work.
