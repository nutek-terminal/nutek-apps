# smap

## Description

smap is a fast and multi-purpose subdomain enumeration tool. It supports multiple sources, user supplied resolvers, DNS wildcard filtering like shuffledns etc.

## install

```bash
brew install smap
```

## sample usage

```
smap 69.52.32.195
```

### sample output

```
Starting Nmap 9.99 ( https://nmap.org ) at 2023-02-14 23:28 CET
Nmap scan report for filetransfer.blackrock.com (69.52.32.195)
Host is up.

PORT    STATE SERVICE  VERSION
21/tcp  open  ftp?     
22/tcp  open  ssh?     
80/tcp  open  http?    
443/tcp open  https?   

Nmap done: 1 IP address (1 host up) scanned in 0.45 seconds
```

## webpage

[https://github.com/s0md3v/Smap](https://github.com/s0md3v/Smap)

## help

```
Smap 0.1.12
Usage: smap <targets here>
TARGET SPECIFICATION:
  Valid targets are hostnames, IP addresses, networks, etc.
  Ex: scanme.nmap.org, microsoft.com/24, 192.168.0.1
  -iL <filename>: Input from list of hosts/networks. Use - as filename to use stdin input.
OUTPUT:
  Specify a file to write the output or use - as filename to write it to stdout (terminal).
  Ex: -oX <filename>
  -oX XML
  -oG Greppable
  -oN Nmap
  -oA All 3 above
  -oJ JSON
  -oS Smap format
  -oP ip:port pairs
```