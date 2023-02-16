# ipcalc

## Description

ipcalc is a command line tool for network address calculations.

## Installation

```bash
brew install ipcalc
```

## Usage

```bash
ipcalc 192.168.0.1/24
```

## Output

```bash
Address:	192.168.0.1
Network:	192.168.0.0/24
Netmask:	255.255.255.0 = 24
Broadcast:	192.168.0.255

Address space:	Private Use
HostMin:	192.168.0.1
HostMax:	192.168.0.254
Hosts/Net:	254
```

## Resources

- [ipcalc](http://jodies.de/ipcalc)

## help

```bash
Usage: ipcalc [OPTION...]
  -c, --check                     Validate IP address
  -r, --random-private=PREFIX     Generate a random private IP network using
                                  the supplied prefix or mask.
  -S, --split=PREFIX              Split the provided network using the
                                  provided prefix/netmask
  -d, --deaggregate=IP1-IP2       Deaggregate the provided address range
  -i, --info                      Print information on the provided IP address
                                  (default)
      --all-info                  Print verbose information on the provided IP
                                  address

Specific info options:
      --reverse-dns               Print network in a the reverse DNS format
  -a, --address                   Display IP address
  -b, --broadcast                 Display calculated broadcast address
  -m, --netmask                   Display netmask for IP
  -n, --network                   Display network address
  -p, --prefix                    Display network prefix
      --minaddr                   Display the minimum address in the network
      --maxaddr                   Display the maximum address in the network
      --addresses                 Display the maximum number of addresses in
                                  the network
      --addrspace                 Display the address space the network
                                  resides on
  -h, --hostname                  Show hostname determined via DNS
  -o, --lookup-host=STRING        Show IP as determined via DNS
  -g, --geoinfo                   Show Geographic information about the
                                  provided IP

Other options:
  -4, --ipv4                      Explicitly specify the IPv4 address family
  -6, --ipv6                      Explicitly specify the IPv6 address family
      --class-prefix              When specified the default prefix will be determined
                                  by the IPv4 address class
      --no-decorate               Print only the requested information
  -j, --json                      JSON output
  -s, --silent                    Don't ever display error messages
  -v, --version                   Display program version
  -?, --help                      Show this help message
      --usage                     Display brief usage message
```