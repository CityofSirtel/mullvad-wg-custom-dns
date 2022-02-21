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

Make sure you have a free slot for a Wireguard key on your account before you create it, the script will generate a new one. 

The -R flag can be used to regenerate keys and get a new IP for your existing config file, replacing the Wireguard key with Mullvad for you. This is what the [app does](https://mullvad.net/en/help/why-wireguard/) and it's best practice to change your internal IP every so often.

```
mullvad-wg-custom-dns -R /etc/wireguard/wg0.conf -a /etc/wireguard/account_number
```

Mullvad goes pretty far out of their way to prevent DNS leaks for normal users, if you care about that and dont know how to anonymize your DNS traffic, use with care.
