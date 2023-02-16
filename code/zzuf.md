# zzuf
multi-purpose fuzzer

zzuf is a transparent application input fuzzer. Its purpose is to find bugs in applications by corrupting their user-contributed data (which more than often comes from untrusted sources on the Internet). It works by intercepting file and network operations and changing random bits in the program’s input. zzuf’s behaviour is deterministic, making it easier to reproduce bugs. Its main areas of use are:

quality assurance: use zzuf to test existing software, or integrate it into your own software’s testsuite
security: very often, segmentation faults or memory corruption issues mean a potential security hole, zzuf helps exposing some of them
code coverage analysis: use zzuf to maximise code coverage
zzuf’s primary target is media players, image viewers and web browsers, because the data they process is inherently insecure, but it was also successfully used to find bugs in system utilities such as objdump.

zzuf is not rocket science: the idea of fuzzing input data is barely new, but zzuf’s main purpose is to make things easier and automated. You can see an old, impressive list of FIXME: go there -> bugs found with zzuf <- from webpage.

## Installation

```bash
brew install zzuf
```

## Usage

```bash

```

## Resources

- [zzuf](http://caca.zoy.org/wiki/zzuf)
- [Basic fuzzing with zzuf YouTube](https://www.youtube.com/watch?v=0ZQ9Zz7Y9qA)
- [Basic usage](http://caca.zoy.org/wiki/zzuf/tutorial1)

## package info

```
Name         : zzuf
Version      : 0.15
Release      : 17.fc37
Architecture : x86_64
Size         : 279 k
Source       : zzuf-0.15-17.fc37.src.rpm
Repository   : @System
From repo    : fedora
Summary      : Transparent application input fuzzer
URL          : http://sam.zoy.org/zzuf/
License      : WTFPL
Description  : zzuf is a transparent application input fuzzer.  It works by
             : intercepting file operations and changing random bits in the program's
             : input.  zzuf's behaviour is deterministic, making it easy to reproduce
             : bugs.
```

## man page

```man
zzuf(1)											General Commands Manual											zzuf(1)

NAME
       zzuf - multiple purpose fuzzer

SYNOPSIS
       zzuf  [-AcdimnqSvxX]  [-s  seed|-s start:stop] [-r ratio|-r min:max] [-f fuzzing] [-D delay] [-j jobs] [-C crashes] [-B bytes] [-t seconds] [-T seconds] [-U seconds] [-M mebibytes] [-b ranges]
       [-p ports] [-P protect] [-R refuse] [-a list] [-l list] [-I include] [-E exclude] [-O opmode] [PROGRAM [ARGS]...]
       zzuf -h | --help
       zzuf -V | --version

DESCRIPTION
       zzuf is a transparent application input fuzzer. It works by intercepting file and network operations and changing random bits in the program's input.  zzuf's behaviour is deterministic, making
       it easy to reproduce bugs.

USAGE
       zzuf  will  run an application specified on its command line, one or several times, with optional arguments, and will report the application's relevant behaviour on the standard error channel,
       eg:

	   zzuf cat /dev/zero

       Flags found after the application name are considered arguments for the application, not for zzuf. For instance, -v below is an argument for cat:

	   zzuf -B 1000 cat -v /dev/zero

       When no program is specified, zzuf simply fuzzes the standard input, as if the cat utility had been called:

	   zzuf < /dev/zero

OPTIONS
   Generic program information
       -h, --help
	      Display a short help message and exit.

       -V, --version
	      Output version information and exit.

   Operating mode
       -f, --fuzzing=mode
	      Select how the input is fuzzed. Valid values for mode are:

	      xor    randomly set and unset bits

	      set    only set bits

	      unset  only unset bits

	      The default value for mode is xor.

       -O, --opmode=mode
	      Use operating mode mode. Valid values for mode are:

	      preload
		     override functions by preloading libzzuf into the executable using the system's dynamic linker

	      copy   temporarily copy files that need to be fuzzed

	      The default value for mode is preload. copy is useful on platforms that do not support dynamic linker injection, for instance when fuzzing a Cocoa application on Mac OS X.

       -s, --seed=seed
       -s, --seed=start:
       -s, --seed=start:stop
	      Specify the random seed to use for fuzzing, or a range of random seeds.  Running zzuf twice with the same random seed will fuzz the files exactly the same way,  even  with  a  different
	      target application. The purpose of this is to use simple utilities such as cat or cp to generate a file that causes the target application to crash.

	      If  a  range  is specified, zzuf will run the application several times, each time with a different seed, and report the behaviour of each run. If no ‘stop’ is specified after ‘:’, zzuf
	      will increment the seed value indefinitely.

       -r, --ratio=ratio
       -r, --ratio=min:max
	      Specify the proportion of bits that will be randomly fuzzed. A value of 0 will not fuzz anything. A value of 0.05 will fuzz 5% of the open files' bits. A value of 1.0 or more will  fuzz
	      all the bytes, theoretically making the input files undiscernible from random data. The default fuzzing ratio is 0.004 (fuzz 0.4% of the files' bits).

	      A range can also be specified. When doing so, zzuf will pick ratio values from the interval. The choice is deterministic and only depends on the interval bounds and the current seed.

       -A, --autoinc
	      Increment	 random	 seed  each  time a new file is opened. This is only required if one instance of the application is expected to open the same file several times and you want to test a
	      different seed each time.

   Output
       -d, --debug
	      Activate the display of debug messages. Can be specified multiple times for increased verbosity.

       -q, --quiet
	      Hide the output of the fuzzed application. This is useful if the application is very verbose but only its exit code or signaled status is really useful to you.

       -v, --verbose
	      Print information during the run, such as the current seed, what processes get run, their exit status, etc.

       -m, --md5
	      Instead of displaying the program's standard output, just print its MD5 digest to zzuf's standard output. The standard error channel is left untouched. See also the -X flag.

       -X, --hex
	      Convert the fuzzed program's standard output to hexadecimal. The standard error channel is left untouched. See also the -m flag.

   Process control
       -B, --max-bytes=n
	      Automatically stop after n bytes have been output.

	      This either terminates child processes that output more than n bytes on the standard output and standard error channels, or stop reading from standard  input  if	 no  program  is  being
	      fuzzed.

	      This is useful to detect infinite loops. See also the -U and -T flags.

       -C, --max-crashes=n
	      Stop forking when at least n children have crashed. The default value is 1, meaning zzuf will stop as soon as one child has crashed. A value of 0 tells zzuf to never stop.

	      Note that zzuf will not kill any remaining children once n is reached. To ensure that processes do not last forever, see the -U flag.

	      A process is considered to have crashed if any signal (such as, but not limited to, SIGSEGV) caused it to exit. If the -x flag is used, this will also include processes that exit with a
	      non-zero status.

	      This option is only relevant if the -s flag is used with a range argument. See also the -t flag.

       -D, --delay=delay
	      Do not launch more than one process every delay seconds. This option should be used together with -j to avoid fork bombs.

       -j, --jobs=jobs
	      Specify the number of simultaneous children that can be run. By default, zzuf only launches one process at a time.

	      This option is only relevant if the -s flag is used with a range argument. See also the -D flag.

       -M, --max-memory=mebibytes
	      Specify the maximum amount of memory, in mebibytes (1 MiB = 1,048,576 bytes), that children are allowed to allocate. This is useful to detect infinite loops that eat up a lot of memory.

	      The value should be set reasonably high so as not to interfer with normal program operation. By default, it is set to 1024 MiB in order to avoid accidental excessive swapping.  To  dis‐
	      able the limitation, set the maximum memory usage to -1 instead.

	      zzuf uses the setrlimit() call to set memory usage limitations and relies on the operating system's ability to enforce such limitations.

       -S, --signal
	      Prevent  children from installing signal handlers for signals that usually cause coredumps. These signals are SIGABRT, SIGFPE, SIGILL, SIGQUIT, SIGSEGV, SIGTRAP and, if available on the
	      running platform, SIGSYS, SIGEMT, SIGBUS, SIGXCPU and SIGXFSZ. Instead of calling the signal handler, the application will simply crash. If you do not want core dumps,  you  should  set
	      appropriate limits with the limit coredumpsize command. See your shell's documentation on how to set such limits.

       -t, --max-time=n
	      Stop forking after n seconds. By default, zzuf runs until the end of the seed range is reached.

	      Note that zzuf will not kill any remaining children once n is reached. To ensure that processes do not last forever, see the -U flag.

	      This option is only relevant if the -s flag is used with a range argument. See also the -C flag.

       -T, --max-cputime=n
	      Automatically terminate child processes that use more than n seconds of CPU time.

	      zzuf  uses the setrlimit() call to set CPU usage limitations and relies on the operating system's ability to enforce such limitations. If the system sends SIGXCPU signals and the appli‐
	      cation catches that signal, it will receive a SIGKILL signal after 5 seconds.

	      This is more accurate than -U because the behaviour should be independent from the system load, but it does not detect processes stuck into infinite select() calls because they use very
	      little CPU time. See also the -B and -U flags.

       -U, --max-usertime=n
	      Automatically terminate child processes that run for more than n seconds. This is useful to detect infinite loops or processes stuck in other situations. See also the -B and -T flags.

       -x, --check-exit
	      Report processes that exit with a non-zero status. By default only processes that crash due to a signal are reported.

   Filtering
       -a, --allow=list
	      Only  fuzz network input for IPs in list, a comma-separated list of IP addresses. If the list starts with !, the flag meaning is reversed and all addresses are fuzzed except the ones in
	      the list.

	      As of now, this flag only understands INET (IPv4) addresses.

	      This option requires network fuzzing to be activated using -n.

       -b, --bytes=ranges
	      Restrict fuzzing to bytes whose offsets in the file are within ranges.

	      Range values start at zero and are inclusive. Use dashes between range values and commas between ranges. If the right-hand part of a range is ommited, it means  end  of	file.  For  in‐
	      stance, to restrict fuzzing to bytes 0, 3, 4, 5 and all bytes after offset 31, use ‘-b0,3-5,31-’.

	      This option is useful to preserve file headers or corrupt only a specific portion of a file.

       -c, --cmdline
	      Only fuzz files whose name is specified in the target application's command line. This is mostly a shortcut to avoid specifying the argument twice:

		  zzuf -c cat file.txt

	      has the same effect as

		  zzuf -I '^file\.txt$' cat file.txt

	      See the -I flag for more information on restricting fuzzing to specific files.

       -E, --exclude=regex
	      Do  not  fuzz  files  whose  name matches the regex regular expression. This option supersedes anything that is specified by the -I flag. Use this for instance if you are unsure of what
	      files your application is going to read and do not want it to fuzz files in the /etc directory.

	      Multiple -E flags can be specified, in which case files matching any one of the regular expressions will be ignored.

       -i, --stdin
	      Fuzz the application's standard input. By default zzuf only fuzzes files.

       -I, --include=regex
	      Only fuzz files whose name matches the regex regular expression. Use this for instance if your application reads configuration files at startup and you only want specific  files	 to  be
	      fuzzed.

	      Multiple -I flags can be specified, in which case files matching any one of the regular expressions will be fuzzed. See also the -c flag.

       -l, --list=list
	      Cherry-pick the list of file descriptors that get fuzzed. The Nth descriptor will really be fuzzed only if N is in list.

	      Values  start at 1 and ranges are inclusive. Use dashes between values and commas between ranges. If the right-hand part of a range is ommited, it means all subsequent file descriptors.
	      For instance, to restrict fuzzing to the first opened descriptor and all descriptors starting from the 10th, use ‘-l1,10-’.

	      Note that this option only affects file descriptors that would otherwise be fuzzed. Even if 10 write-only descriptors are opened at the beginning of the program, only the next  descrip‐
	      tor with a read flag will be the first one considered by the -l flag.

       -P, --protect=list
	      Protect a list of characters so that if they appear in input data that would normally be fuzzed, they are left unmodified instead.

	      Characters in list can be expressed verbatim or through escape sequences.	 The sequences interpreted by zzuf are:

	      \n     new line

	      \r     return

	      \t     tabulation

	      \NNN   the byte whose octal value is NNN

	      \xNN   the byte whose hexadecimal value is NN

	      \\     backslash (‘\’)

	      You can use ‘-’ to specify ranges. For instance, to protect all bytes from ‘\001’ to ‘/’, use ‘-P '\001-/'’.

	      The  statistical	outcome	 of  this option should not be overlooked: if characters are protected, the effect of the ‘-r’ flag will vary depending on the data being fuzzed. For instance,
	      asking to fuzz 1% of input bits (-r0.01) and to protect lowercase characters (-P a-z) will result in an actual average fuzzing ratio of 0.9% with truly random  data,  0.3%  with	 random
	      ASCII data and 0.2% with standard English text.

	      See also the -R flag.

       -R, --refuse=list
	      Refuse  a	 list  of  characters by not fuzzing bytes that would otherwise be changed to a character that is in list. This does not prevent characters from appearing in the output if the
	      original byte was already in list.

	      See the -P option for a description of list.

   Network
       -n, --network
	      Fuzz the application's network input. By default zzuf only fuzzes files.

	      Only INET (IPv4) and INET6 (IPv6) connections are fuzzed. Other protocol families are not yet supported.

       -p, --ports=ranges
	      Only fuzz network ports that are in ranges. By default zzuf fuzzes all ports. The port considered is the listening port if the socket is listening and the destination port if the socket
	      is connecting, because most of the time the source port cannot be predicted.

	      Range  values  start  at	zero  and are inclusive. Use dashes between range values and commas between ranges. If the right-hand part of a range is ommited, it means end of file. For in‐
	      stance, to restrict fuzzing to the HTTP and HTTPS ports and to all unprivileged ports, use ‘-p80,443,1024-’.

	      This option requires network fuzzing to be activated using -n.

DIAGNOSTICS
       Exit status is zero if no child process crashed. If one or several children crashed, zzuf exits with status 1.

EXAMPLES
       Fuzz the input of the cat program using default settings:

	   zzuf cat /etc/motd

       Fuzz 1% of the input bits of the cat program using seed 94324:

	   zzuf -s94324 -r0.01 cat /etc/motd

       Fuzz the input of the cat program but do not fuzz newline characters and prevent non-ASCII characters from appearing in the output:

	   zzuf -P '\n' -R '\x00-\x1f\x7f-\xff' cat /etc/motd

       Fuzz the input of the convert program, using file foo.jpeg as the original input and excluding .xml files from fuzzing (because convert will also open its own XML configuration files and we do
       not want zzuf to fuzz them):

	   zzuf -E '\.xml$' convert foo.jpeg -format tga /dev/null

       Fuzz  the input of VLC, using file movie.avi as the original input and restricting fuzzing to filenames that appear on the command line (-c), then generate fuzzy-movie.avi which is a file that
       can be read by VLC to reproduce the same behaviour without using zzuf:

	   zzuf -c -s87423 -r0.01 vlc movie.avi
	   zzuf -c -s87423 -r0.01 <movie.avi >fuzzy-movie.avi
	   vlc fuzzy-movie.avi

       Fuzz between 0.1% and 2% of MPlayer's input bits (-r0.001:0.02) with seeds 0 to 9999 (-s0:10000), preserving the AVI 4-byte header by restricting fuzzing to offsets after 4  (-b4-),  disabling
       its  standard  output  messages (-q), launching up to five simultaneous child processes (-j5) but waiting at least half a second between launches (-D0.5), killing MPlayer if it takes more than
       one minute to read the file (-T60) and disabling its SIGSEGV signal handler (-S):

	   zzuf -c -r0.001:0.02 -s0:10000 -b4- -q -j5 -D0.5 -T60 -S \
	     mplayer -benchmark -vo null -fps 1000 movie.avi

       A more advanced VLC fuzzing example, stopping only at the first crash:

	   zzuf -j4 -vqc -r0.000001:0.01 -s0: vlc -v -I dummy movie.avi \
	      --sout '#transcode{acodec=s16l,vcodec=I420}:dummy' vlc:quit

       Create an HTML-like file that loads 200 times the same hello.jpg image and open it in Firefox™ in auto-increment mode (-A):

	   seq -f '<img src="hello.jpg#%g">' 1 200 > hello.html
	     (or: jot -w '<img src="hello.jpg#%d">' 200 1 > hello.html)
	   zzuf -A -I 'hello[.]jpg' -r0.001 firefox hello.html

       Run a simple HTTP redirector on the local host using socat and corrupt each network connection (-n) in a different way (-A) after one megabyte of data was received on it (-b1000000-):

	    zzuf -n -A -b1000000- \
	      socat TCP4-LISTEN:8080,reuseaddr,fork TCP4:192.168.1.42:80

       Browse the intarweb (-n) using Firefox™ without fuzzing local files (-E.) or non-HTTP connections (-p80,8010,8080), preserving the beginning of the data sent with each HTTP response  (-b4000-)
       and using another seed on each connection (-A):

	   zzuf -r 0.0001 -n -E. -p80,8010,8080 -b4000- -A firefox

RESTRICTIONS
       Due to zzuf using shared object preloading (LD_PRELOAD, _RLD_LIST, DYLD_INSERT_LIBRARIES, etc.) to run its child processes, it will fail in the presence of any mechanism that disables preload‐
       ing. For instance setuid root binaries will not be fuzzed when run as an unprivileged user.

       For the same reasons, zzuf will also not work with statically linked binaries. Bear this in mind when using zzuf on the OpenBSD platform, where cat, cp and dd are static binaries.

       Though best efforts are made, identical behaviour for different versions of zzuf is not guaranteed. The reproducibility for subsequent calls on different operating systems and	with  different
       target programs is only guaranteed when the same version of zzuf is being used.

BUGS
       zzuf probably does not behave correctly with 64-bit offsets.

       It is not yet possible to insert or drop bytes from the input, to fuzz according to the file format, to swap bytes, etc. More advanced fuzzing methods are planned.

       As of now, zzuf does not really support multithreaded applications. The behaviour with multithreaded applications where more than one thread does file descriptor operations is undefined.

HISTORY
       zzuf started its life in 2002 as the streamfucker tool, a small multimedia stream corrupter used to find bugs in the VLC media player.

SEE ALSO
       libzzuf(3), zzat(1)

AUTHOR
       Copyright © 2002-2015 Sam Hocevar <sam@hocevar.net>.

       zzuf  and  this manual page are free software. They come without any warranty, to the extent permitted by applicable law. You can redistribute them and/or modify them under the terms of the Do
       What the Fuck You Want to Public License, Version 2, as published by the WTFPL Task Force. See http://www.wtfpl.net/ for more details.

       zzuf's webpage can be found at http://caca.zoy.org/wiki/zzuf.  An overview of the architecture and inner works is at http://caca.zoy.org/wiki/zzuf/internals.

zzuf 0.15										       2015-01-06											zzuf(1)
```