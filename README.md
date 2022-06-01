# certbot-dns-cloudflare-cname
[![PyPI version](https://badge.fury.io/py/certbot-dns-cloudflare-cname.svg)](https://badge.fury.io/py/certbot-dns-cloudflare-cname)
![CodeQL](https://github.com/rsc-dev/certbot-dns-cloudflare-cname/workflows/CodeQL/badge.svg)

Cloudflare DNS Authenticator plugin for Certbot with support for CNAME aliasing.  
It supports [DNS-01 challenge](https://letsencrypt.org/docs/challenge-types/#dns-01-challenge) with CNAME aliasing described [here](https://www.eff.org/deeplinks/2018/02/technical-deep-dive-securing-automation-acme-dns-challenge-validation).

It is based on official [Certbot Cloudflare plugin](https://github.com/certbot/certbot/tree/master/certbot-dns-cloudflare) ([documentation](https://certbot-dns-cloudflare.readthedocs.io/en/stable/)).

## Installation ##
### SNAP

[SNAP link](https://snapcraft.io/certbot-dns-cloudflare-cname)
```bash
snap install certbot-dns-cloudflare-cname
snap set certbot trust-plugin-with-root=ok
snap connect certbot:plugin certbot-dns-cloudflare-cname
snap connect certbot-dns-cloudflare-cname:certbot-metadata certbot:certbot-metadata
```

### PyPI
[PyPI link](https://pypi.org/project/certbot-dns-cloudflare-cname/)
```bash
pip install certbot-dns-cloudflare-cname
```



## Command Line Options ##
Argument | Description
-|-
--dns-cloudflare-cname-credentials | Cloudflare [credentials](https://certbot-dns-cloudflare.readthedocs.io/en/stable/#credentials) INI file. (Required)
--dns-cloudflare-cname-follow-cnames | If true, authenticator will try to resolve validation name. (Default: true)
--dns-cloudflare-cname-propagation-seconds | The number of seconds to wait for DNS to propagate before asking the ACME server to verify the DNS record. (Default: 10)


## Usage ##
```bash
certbot certonly --dry-run -a dns-cloudflare-cname --dns-cloudflare-cname-credentials /var/cloudflare.ini -d subdomain.example.com
```
