# p0f

## Description
What's this?
P0f is a tool that utilizes an array of sophisticated, purely passive traffic fingerprinting mechanisms to identify the players behind any incidental TCP/IP communications (often as little as a single normal SYN) without interfering in any way. Version 3 is a complete rewrite of the original codebase, incorporating a significant number of improvements to network-level fingerprinting, and introducing the ability to reason about application-level payloads (e.g., HTTP).

Some of p0f's capabilities include:

Highly scalable and extremely fast identification of the operating system and software on both endpoints of a vanilla TCP connection - especially in settings where NMap probes are blocked, too slow, unreliable, or would simply set off alarms.

Measurement of system uptime and network hookup, distance (including topology behind NAT or packet filters), user language preferences, and so on.

Automated detection of connection sharing / NAT, load balancing, and application-level proxying setups.

Detection of clients and servers that forge declarative statements such as X-Mailer or User-Agent.

The tool can be operated in the foreground or as a daemon, and offers a simple real-time API for third-party components that wish to obtain additional information about the actors they are talking to.

Common uses for p0f include reconnaissance during penetration tests; routine network monitoring; detection of unauthorized network interconnects in corporate environments; providing signals for abuse-prevention tools; and miscellanous forensics.

You can read more about its design and operation in this document. In one form or another, earlier versions of p0f are used in a wide variety of projects, including pfsense, Ettercap, PRADS, amavisd, milter, postgrey, fwknop, Satori, the OpenBSD firewall, and an assortment of commercial tools.

Fun fact: The idea for p0f dates back to June 10, 2000. Today, almost all applications that do passive OS fingerprinting either simply reuse p0f for TCP-level checks (Ettercap, Disco, PRADS, Satori), or use inferior approaches that, for example, pay no attention to the intricate relationship between host's window size and MTU (SinFP).

## install

```
brew install p0f
```

## package info

```
Name         : p0f
Version      : 3.09b
Release      : 14.fc37
Architecture : x86_64
Size         : 286 k
Source       : p0f-3.09b-14.fc37.src.rpm
Repository   : @System
From repo    : fedora
Summary      : Versatile passive OS fingerprinting tool
URL          : http://lcamtuf.coredump.cx/p0f.shtml
License      : LGPLv2+
Description  : P0f is a versatile passive OS fingerprinting tool. P0f can identify the
             : system on machines that talk thru or near your box. p0f will also check
             : masquerading and firewall presence, the distance to the remote system and its
             : uptime, other guy's network hookup (DSL, OC3, avian carriers) and his ISP.
```

## sample usage

```
sudo p0f -i eth0
```

## readme

```
Usage: p0f [ ...options... ] [ 'filter rule' ]

Network interface options:

  -i iface  - listen on the specified network interface
  -r file   - read offline pcap data from a given file
  -p        - put the listening interface in promiscuous mode
  -L        - list all available interfaces

Operating mode and output settings:

  -f file   - read fingerprint database from 'file' (/etc/p0f/p0f.fp)
  -o file   - write information to the specified log file
  -s name   - answer to API queries at a named unix socket
  -u user   - switch to the specified unprivileged account and chroot
  -d        - fork into background (requires -o or -s)

Performance-related options:

  -S limit  - limit number of parallel API connections (20)
  -t c,h    - set connection / host cache age limits (30s,120m)
  -m c,h    - cap the number of active connections / hosts (1000,10000)

Optional filter expressions (man tcpdump) can be specified in the command
line to prevent p0f from looking at incidental network traffic.

Problems? You can reach the author at <lcamtuf@coredump.cx>.
```