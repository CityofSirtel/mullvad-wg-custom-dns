A simple bash script to create Mullvad Wireguard config files with no DNS hijacking. Credit goes to [this blog post](https://schnerring.net/blog/use-custom-dns-servers-with-mullvad-and-any-wireguard-client/) for the app api used to create it.

I use it for running a local recursive DNS server through the vpn, default configs hijack all DNS requests.

```
mullvad-wg-custom-dns -s SERVERNAME -a ACCOUNT_NUMBER -d DNS_IP -o OUTPUT_FILE
```
Get the server name from Mullvad [here](https://mullvad.net/en/servers/), ie at5-wireguard

```
mullvad-wg-custom-dns -s at5-wireguard -a ACCOUNT_NUMBER -d '127.0.0.1' -o wg0.conf
```
Wireguard also accepts comma separated lists of IPs and search domains for DNS

```
'127.0.0.1, 8.8.8.8, local.example.com'
```

Make sure you have a free slot for a Wireguard key on your account before you create it, the script will generate a new one for you.

Mullvad goes pretty far out of their way to prevent DNS leaks for normal users, if you care about that and dont know how to anonymize your DNS traffic, use with care.
