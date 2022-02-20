A simple bash script to create Mullvad Wireguard config files with no DNS hijacking. Credit goes to [this blog post](https://schnerring.net/blog/use-custom-dns-servers-with-mullvad-and-any-wireguard-client/) for the app api used to create it.

I use it for running a local recursive DNS server through the vpn, default configs hijack all DNS requests.

```
mullvad-wg-customdns -s SERVERNAME -p SERVER_PUBKEY -a ACCOUNT_NUMBER -d DNS_IP > wg.conf
```
Get the server name and pubkey from Mullvad [here](https://mullvad.net/en/servers/), ie at5-wireguard.

```
mullvad-wg-customdns -s at5-wireguard -p jJVG/lv7RikDG0FMsV3WJgfot5XecPm9aHDrYvU+NAM= -a ACCOUNT_NUMBER -d DNS_IP > wg.conf
```

Make sure you have a free slot for a Wireguard key on your account before you create it, the script will generate a new one for you
