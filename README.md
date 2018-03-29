# Dyndns on an Ubiqiti EdgeRouter using GleSYS DNS API

This script can runs periodically on my EdgeRouter to get the current
address of eth0. It then updates a DNS record using the GleSYS DNS API.

Information about the GleSYS API is available here:
https://github.com/glesys/api/wiki/Api-Introduction

## Dependencies

This script depends on the utility jq (https://stedolan.github.io/jq/) to be
present on the system. I needed this functionality on my Ubiqiti EdgeRouter and
the utility jq happened to be available on it.

## How to use

You need an account at Glesys. Login and generate an API token. This
API key needs a few domain permissions:

- listrecords
- updaterecord

Remember to also give your own IP address access to use this token, or use
0.0.0.0/0 to accept all IP addresses.

Run dyndns_glesys.sh on your EdgeRouter like this:

```
export GLESYS_USER=<GleSYS username>
export GLESYS_TOKEN=<GleSYS API token>
dyndns_glesys.sh home.example.com
```

You will probably want to run the script once in a while. This can be done
by using the task-scheduler. Google will help you to get there.
