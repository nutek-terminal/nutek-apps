# whatmask

## Description

whatmask is a tool to calculate the netmask from a given IP address and netmask.

## Installation

```bash
brew install whatmask
```

## Usage

```bash
whatmask 192.168.0.1/24
whatmask 255.255.255.0
```

## Resources

- [whatmask](http://www.laffeycomputer.com/whatmask.html)

## help

```bash
Whatmask(1)											Network											    Whatmask(1)

NAME
       whatmask - Subnet mask notation conversion tool.

SYNTAX
       whatmask <netmask or ip/netmask>
       see the Examples section below

DESCRIPTION
       Whatmask is a small C program that will help you with network settings.

       Whatmask	 can  work  in two modes.  The first mode is to invoke Whatmask with only a subnet mask as the argument. In this mode Whatmask will echo back the subnet mask in four formats, plus the
       number of useable addresses in the range.

       Netmask Notations supported:
	Name		      Example

	CIDR			     /24
	Netmask		   255.255.255.0
	Netmask (hex)	      0xffffff00
	Wilcard Bits	       0.0.0.255

       The above notations are all identical.  CIDR notation commonly has a "/" in front of the number (representing the number of bits).  Whatmask can accept these notations with or without a slash.
       This notation is used more and more recently. A lot of popular routers and software support this notation.

       Netmask notation is pretty much the standard old-school way of doing it. It is supported by most systems (Un*x, Win, Mac, etc.).

       Netmask (Hex) is the hexadecimal representation of the netmask. Many implementations of ifconfig use this notation

       Wilcard Bits are similar to the netmask, but they are the logical not of the netmask. This notation is used by a number of popular routers (and nobody knows why...).

       To  use	Whatmask  in the first mode simply type "whatmask <notation>" The notation can be in any of the four formats and Whatmask will automagically figure out what it is and display all four
       notations.

       To use Whatmask in  its	second	mode  execute  Whatmask	 with  any  ip	address	 within	 the  subnet,  followed	 by  a	slash  ('/'),  followed	 by  the  subnet  mask	in  any	 format.  (e.g.
       192.168.0.23/255.255.255.224, or 192.168.0.23/27) Put no spaces in the argument.

       Whatmask will echo back the following:

       - The netmask in the following formats: CIDR, Netmask, Netmask (Hex), Wildcard Bits

       - The Network Address

       - The Broadcast Address

       - The number of Usable IP Addresses

       - The First Usable IP Address

       - The Last Usable IP Address

	      (Whatmask assumes that the Broadcast address is the highest address in the subnet. This is the most common configuration.)

OPTIONS
       <no options> see above and below for usage.

EXAMPLES
       Examples of how Whatmask works:

	    myhost> whatmask /26

	    ---------------------------------------------
		    TCP/IP SUBNET MASK EQUIVALENTS
	    ---------------------------------------------
	    CIDR = .....................: /26
	    Netmask = ..................: 255.255.255.192
	    Netmask (hex) = ............: 0xffffffc0
	    Wildcard Bits = ............: 0.0.0.63
	    Usable IP Addresses = ......: 62

	    myhost> whatmask 255.255.192.0

	    ---------------------------------------------
		    TCP/IP SUBNET MASK EQUIVALENTS
	    ---------------------------------------------
	    CIDR = .....................: /18
	    Netmask = ..................: 255.255.192.0
	    Netmask (hex) = ............: 0xffffc000
	    Wildcard Bits = ............: 0.0.63.255
	    Usable IP Addresses = ......: 16,382

	    myhost> whatmask 0xffffffe0

	    ---------------------------------------------
		    TCP/IP SUBNET MASK EQUIVALENTS
	    ---------------------------------------------
	    CIDR = .....................: /27
	    Netmask = ..................: 255.255.255.224
	    Netmask (hex) = ............: 0xffffffe0
	    Wildcard Bits = ............: 0.0.0.31
	    Usable IP Addresses = ......: 30

	    myhost> whatmask 0.0.0.31

	    ---------------------------------------------
		    TCP/IP SUBNET MASK EQUIVALENTS
	    ---------------------------------------------
	    CIDR = .....................: /27
	    Netmask = ..................: 255.255.255.224
	    Netmask (hex) = ............: 0xffffffe0
	    Wildcard Bits = ............: 0.0.0.31
	    Usable IP Addresses = ......: 30

	    myhost> whatmask 192.168.165.23/19

	    ------------------------------------------------
			 TCP/IP NETWORK INFORMATION
	    ------------------------------------------------
	    IP Entered = ..................: 192.168.165.23
	    CIDR = ........................: /19
	    Netmask = .....................: 255.255.224.0
	    Netmask (hex) = ...............: 0xffffe000
	    Wildcard Bits = ...............: 0.0.31.255
	    ------------------------------------------------
	    Network Address = .............: 192.168.160.0
	    Broadcast Address = ...........: 192.168.191.255
	    Usable IP Addresses = .........: 8,190
	    First Usable IP Address = .....: 192.168.160.1
	    Last Usable IP Address = ......: 192.168.191.254

	    myhost> whatmask 192.168.0.13/255.255.255.0

	    ------------------------------------------------
			 TCP/IP NETWORK INFORMATION
	    ------------------------------------------------
	    IP Entered = ..................: 192.168.0.13
	    CIDR = ........................: /24
	    Netmask = .....................: 255.255.255.0
	    Netmask (hex) = ...............: 0xffffff00
	    Wildcard Bits = ...............: 0.0.0.255
	    ------------------------------------------------
	    Network Address = .............: 192.168.0.0
	    Broadcast Address = ...........: 192.168.0.255
	    Usable IP Addresses = .........: 254
	    First Usable IP Address = .....: 192.168.0.1
	    Last Usable IP Address = ......: 192.168.0.254

	    myhost> whatmask 192.168.0.113/0xffffffe0

	    ------------------------------------------------
			 TCP/IP NETWORK INFORMATION
	    ------------------------------------------------
	    IP Entered = ..................: 192.168.0.113
	    CIDR = ........................: /27
	    Netmask = .....................: 255.255.255.224
	    Netmask (hex) = ...............: 0xffffffe0
	    Wildcard Bits = ...............: 0.0.0.31
	    ------------------------------------------------
	    Network Address = .............: 192.168.0.96
	    Broadcast Address = ...........: 192.168.0.127
	    Usable IP Addresses = .........: 30
	    First Usable IP Address = .....: 192.168.0.97
	    Last Usable IP Address = ......: 192.168.0.126

	    myhost> whatmask 192.168.0.169/0.0.0.127

	    ------------------------------------------------
			 TCP/IP NETWORK INFORMATION
	    ------------------------------------------------
	    IP Entered = ..................: 192.168.0.169
	    CIDR = ........................: /25
	    Netmask = .....................: 255.255.255.128
	    Netmask (hex) = ...............: 0xffffff80
	    Wildcard Bits = ...............: 0.0.0.127
	    ------------------------------------------------
	    Network Address = .............: 192.168.0.128
	    Broadcast Address = ...........: 192.168.0.255
	    Usable IP Addresses = .........: 126
	    First Usable IP Address = .....: 192.168.0.129
	    Last Usable IP Address = ......: 192.168.0.254

BUGS
       Report bugs to <software@laffeycomputer.com>

CONTRIBUTORS
       Original code:
	      Joe Laffey <software@laffeycomputer.com>

       Assistance with Manpage and Packaging:
	      David Wirch <kuma@linuxboxen.org>

       Many thanks to the beta testers and users who sent in valuable feedback!

UPDATES
       Official Whatmask website:
	      http://www.laffeycomputer.com/whatmask.html

LAFFEY Computer Imaging									      Nov 14, 2003										    Whatmask(1)
```