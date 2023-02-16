# termshark

## Description

Termshark is a terminal UI for tshark, inspired by Wireshark.

## Installation

```bash
brew install termshark
```

## Usage

Capture ping packets on interface eth0:
```bash
termshark -i en0
```

Inspect a local pcap:
```
termshark -r test.pcap
```

## Resources

- [User Guide](https://github.com/gcla/termshark/blob/master/docs/UserGuide.md)

## help

```bash
termshark v2.4.0

A wireshark-inspired terminal user interface for tshark. Analyze network traffic interactively from your terminal.
See https://termshark.io for more information.

Usage:
  termshark [FilterOrPcap]

Application Options:
  -i=<interfaces>                                            Interface(s) to read.
  -r=<infile/fifo>                                           Pcap file/fifo to read. Use - for stdin.
  -w=<outfile>                                               Write raw packet data to outfile.
  -d=<layer type>==<selector>,<decode-as protocol>           Specify dissection of layer type.
  -D                                                         Print a list of the interfaces on which termshark can capture.
  -Y=<displaY filter>                                        Apply display filter.
  -f=<capture filter>                                        Apply capture filter.
  -t=<timestamp format>[a|ad|adoy|d|dd|e|r|u|ud|udoy]        Set the format of the packet timestamp printed in summary lines.
      --tty=<tty>                                            Display the UI on this terminal.
  -C, --profile=<profile>                                    Start with this configuration profile.
      --pass-thru=[auto|true|false]                          Run tshark instead (auto => if stdout is not a tty). (default: auto)
      --log-tty                                              Log to the terminal.
  -h, --help                                                 Show this help message.
  -v, --version                                              Show version information.

Arguments:
  FilterOrPcap:                                              Filter (capture for iface, display for pcap), or pcap to read.

If --pass-thru is true (or auto, and stdout is not a tty), tshark will be
executed with the supplied command-line flags. You can provide
tshark-specific flags and they will be passed through to tshark (-n, -d, -T,
etc). For example:

$ termshark -r file.pcap -T psml -n | less
```