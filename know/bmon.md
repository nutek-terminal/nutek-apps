# bmon

## Description

bmon is a tool for monitoring network interface bandwidth, discards, errors, and more.

## install

```bash
brew install bmon
```

## sample usage

```bash
bmon
```

## website

[https://github.com/tgraf/bmon](https://github.com/tgraf/bmon)

## man page

```
bmon(8)												  bmon												bmon(8)

NAME
       bmon - bandwidth monitor and rate estimator

SYNOPSIS
       bmon [--show-all] [--use-si] [--input=MODULE] [--output=MODULE] [OPTIONS...]

DESCRIPTION
       bmon  is a monitoring and debugging tool to capture networking related statistics and prepare them visually in a human friendly way. It features various output methods including an interactive
       curses user interface and a programmable text output for scripting.

OPTIONS
	-h, --help
	   Prints a short help text and exits.

	-V, --version
	   Prints the versioning identifier and exits.

	-i, --input=MODULE[:OPTIONS][,MODULE...]
	   Set list of input modules to load and use. Multiple modules can be used in parallel. bmon automatically loads a useful and working input module by default. See INPUT MODULES for  more  de‐
	   tails.

	-o, --outputMODULE[:OPTIONS][,MODULE...]
	   Set list of output modules to load and use. Multiple modules can be used in parallel. By default, bmon will use the curses output mode, if that is not available due to an incompatible con‐
	   sole it will fall back to a simple text mode. See OUTPUT MODULES for more details.

	-U, --use-si
	   Use SI unit system (1KB = 1'000 bytes) instead of 1KB = 1'024 bytes.

	-f, --configfile=FILE
	   Set alternative path to configuration file.

	-p, --policy=POLICY
	   Set policy defining which network interfaces to display. See INTERFACE SELECTION for more details.

	-a, --show-all=
	   Display all interfaces, even interface that are administratively down.

	-r, --read-interval=FLOAT
	   Set interval in seconds in which input modules read statistics from their source. The default is 1.0 seconds.

	-R, --rate-interval=FLOAT
	   Set interval in seconds in which the rate per counter is calculated.	 The default is 1.0 seconds.

	-b, --use-bit
	   Show rates in bits per second instead of bytes per second.

	-L, --lifetime=FLOAT
	   Set lifetime of an element in seconds before it is no longer displayed without receiving any statistical updates. The default is 30 seconds.

INPUT MODULES
       Input modules provide statistical data about elements. Each element consists of attributes which represents a counter, a rate, or a percentage. Elements may carry additional child elements  to
       represent a hierarchy. Each element is assigned to a group defined by the input module. Input modules are polled in the frequence of the configured read interval.

       The following input modules are available:

       netlink
	      Uses the Netlink protocol to collect interface and traffic control statistics from the kernel. This is the default input module.

       proc   Reads  interface	statistics  from the /proc/net/dev file. This is considered a legacy interface and provided for backwards compatibily reasons. This is a fallback module if the Netlink
	      interface is not available.

       dummy  Programmable input module for debugging and testing purposes.

       null   No data collected.

       To receive additional information about a module, run the module with the "help" option set like this:

	   bmon -i netlink:help

       See MODULE CONFIGURATION for more details.

OUTPUT MODULES
       Output modules display or export the statistical data collected by input modules. Multiple output modules can be run at the same time. bmon will not prevent possible conflicts such as multiple
       output modules writing to the console.

       The following output modules exist:

       curses Interactive curses based text user interface providing real time rate estimations and a graphical representatio nof each attribute. Press '?'  to display the quick reference guide. This
	      is the default output mode.

       ascii  Simple programmable text output intended for human consumption. Capable of printing list of interfaces, detailed counters and graphs to the console. This is the default fallback	 output
	      mode if curses is not available.

       format Fully scriptable output mode inteded for consumption by other programs.  See the module help text for additional information.

       null   Disable output.

       To receive additional information about a module, run the module with the "help" option set like this:

	   bmon -o curses:help

       See MODULE CONFIGURATION for more details.

MODULE CONFIGURATION
       The syntax to configure modules is as follows:

	   ARGUMENT ::= mod1[:OPTS][,mod2[:OPTS]...]
	   OPTS	    ::= OPTION[;OPTION...]
	   OPTION   ::= option[=value]

       Run the module with option "help" to receive the list of options for each module:

	   bmon -i module:help

INTERFACE SELECTION
       The following syntax is used to define the interface selection policy:

	   SELECTION ::= NAME[,NAME[,...]]
	   NAME	     ::= [!]interface

       The interface name may contain the character '*' which will act as a wildcard and represents any number of any character type, e.g. eth*, h*0, ...

       Examples:

	   lo,eth0,eth1
	   eth*,!eth0

EXAMPLES
       To run bmon in curses mode monitoring the interfaces eth0 and eth1:

	   bmon -p eth0,eth1 -o curses

       To run bmon in format mode, monitoring any eth* interfaces, with a specified format string:

	   bmon -p 'eth*' -o format:fmt='$(element:name) $(attr:rxrate:packets)\n'

FILES
       /etc/bmon.conf
       $HOME/.bmonrc

SEE ALSO
       ip(8), netstat(8), ifconfig(8), netlink(7),

AUTHOR
       Thomas Graf <tgraf@suug.ch> among others

Bandwidth Monitor																						bmon(8)
```