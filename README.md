# Hexonet DNS module for Caddy

This package contains a DNS provider module for [Caddy](https://github.com/caddyserver/caddy). It can be used to manage DNS records with Hexonet accounts.

## Caddy module name

```
dns.providers.hexonet
```

## Config examples

To use this module for the ACME DNS challenge, [configure the ACME issuer in your Caddy JSON](https://caddyserver.com/docs/json/apps/tls/automation/policies/issuer/acme/) like so:

```json
{
  "module": "acme",
  "challenges": {
    "dns": {
      "provider": {
        "name": "hexonet",
        "username": "YOUR_HEXONET_USERNAME",
        "password": "YOUR_HEXONET_PASSWORD"
      }
    }
  }
}
```

or with the Caddyfile:

```
your.domain.com {
  respond "Hello World"	# replace with whatever config you need...
  tls {
    dns hexonet {env.YOUR_HEXONET_USERNAME} {env.YOUR_HEXONET_PASSWORD}
  }
}
```

You can replace `{env.YOUR_HEXONET_USERNAME}` `{env.YOUR_HEXONET_PASSWORD}` with the actual auth token if you prefer to put it directly in your config instead of an environment variable.

## Authenticating

See [the associated README in the libdns package](https://github.com/tojjx/libdns-hexonet) for important information about credentials.
