# nethogs

## Description

NetHogs is a small 'net top' tool. Instead of breaking the traffic down per protocol or per subnet, like most tools do, it groups bandwidth by process.

NetHogs does not rely on a special kernel module to be loaded. If there's suddenly a lot of network traffic, you can fire up NetHogs and immediately see which PID is causing this. This makes it easy to identify programs that have gone wild and are suddenly taking up your bandwidth.

Since NetHogs heavily relies on /proc, most features are only available on Linux. NetHogs can be built on Mac OS X and FreeBSD, but it will only show connections, not processes.

## install

```
brew install nethogs
```

## sample usage

```
sudo nethogs
```

## package info

```
Name         : nethogs
Version      : 0.8.7
Release      : 2.fc37
Architecture : x86_64
Size         : 86 k
Source       : nethogs-0.8.7-2.fc37.src.rpm
Repository   : @System
From repo    : fedora
Summary      : A tool resembling top for network traffic
URL          : https://github.com/raboof/nethogs/
License      : GPL+
Description  : NetHogs is a small "net top" tool.
             : 
             : Instead of breaking the traffic down per protocol or per subnet, like
             : most such tools do, it groups bandwidth by process and does not rely
             : on a special kernel module to be loaded.
             : 
             : So if there's suddenly a lot of network traffic, you can fire up
             : NetHogs and immediately see which PID is causing this, and if it's
             : some kind of spinning process, kill it.
```

## man page

```
NETHOGS(8)										System Manager's Manual										     NETHOGS(8)

NAME
       nethogs - Net top tool grouping bandwidth per process

SYNOPSIS
       nethogs [-V] [-h] [-x] [-d seconds] [-v mode] [-c count] [-t] [-p] [-s] [-a] [-l] [-f filter] [-C] [-b] [-g period] [-P pid] [device(s)]

DESCRIPTION
       NetHogs	is  a  small  'net top' tool. Instead of breaking the traffic down per protocol or per subnet, like most such tools do, it groups bandwidth by process - and does not rely on a special
       kernel module to be loaded. So if there's suddenly a lot of network traffic, you can fire up NetHogs and immediately see which PID is causing this, and if it's some kind of  spinning  process,
       kill it.

   Options
       -V     prints version.

       -h     prints available commands usage.

       -x     bughunt mode - implies tracemode.

       -d     delay for update refresh rate in seconds. default is 1.

       -v     view mode (0 = KB/s, 1 = total KB, 2 = total B, 3 = total MB, 4 = MB/s, 5 = GB/s). default is 0.

       -c     number of updates. default is 0 (unlimited).

       -t     tracemode.

       -p     sniff in promiscuous mode (not recommended).

       -s     sort output by sent column.

       -l     display command line.

       -a     monitor all devices, even loopback/stopped ones.

       -C     capture TCP and UDP.

       -b     Display the program basename.

       -g     garbage collection period in number of refresh. default is 50.

       -P     Show only processes with the specified pid(s).

       -f     EXPERIMENTAL: specify string pcap filter (like tcpdump). This may be removed or changed in a future version.

	      device(s)
	      to monitor. default is all interfaces up and running excluding loopback

INTERACTIVE CONTROL
       q      quit

       s      sort by SENT traffic

       r      sort by RECEIVED traffic

       l      display command line

       b      display the program basename

       m      switch between total (KB, B, MB) and throughput (KB/s, MB/s, GB/s) mode

RUNNING WITHOUT ROOT
       In order to be run by an unprivileged user, nethogs needs the cap_net_admin and cap_net_raw capabilities. These can be set on the executable by using the setcap(8) command, as follows:

	   sudo setcap "cap_net_admin,cap_net_raw+pe" /usr/local/sbin/nethogs

Notes
       1.  When using the -P <pid> option, in a case where a process exited (normally or abruptly), Nethogs does not track that it exited. So, the operating system might create a new process (for an‐
       other program) with the same pid. In this case, this new process will be shown by Nethogs.

SEE ALSO
       netstat(8) tcpdump(1) pcap(3)

AUTHOR
       Written by Arnout Engelen <arnouten@bzzt.net>.

											    14 February 2004										     NETHOGS(8)
```