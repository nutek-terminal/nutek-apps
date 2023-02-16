# radare2

## Description

Radare2 is a reverse engineering framework.

## Installation

```bash
brew install radare2
```

## Usage

```bash
r2 /bin/ls
```

## Resources

- [radare2](https://radare.org/r/)
- [radare2 Book](https://radare.gitbooks.io/radare2book/content/)

## help

```bash
r2 /bin/bash
Warning: run r2 with -e bin.cache=true to fix relocations in disassembly
 -- The only way to learn a new programming language is by writing programs in it.
[0x00031d80]> ?
[0x00031d80]> ?
Usage: [.][times][cmd][~grep][@[@iter]addr!size][|>pipe] ; ...
Append '?' to any char command to get detailed help
Prefix with number to repeat command N times (f.ex: 3x)
| %var=value              alias for 'env' command
| *[?] off[=[0x]value]    pointer read/write data/values (see ?v, wx, wv)
| (macro arg0 arg1)       manage scripting macros
| .[?] [-|(m)|f|!sh|cmd]  Define macro or load r2, cparse or rlang file
| ,[?] [/jhr]             create a dummy table import from file and query it to filter/sort
| _[?]                    Print last output
| =[?] [cmd]              send/listen for remote commands (rap://, raps://, udp://, http://, <fd>)
| <[...]                  push escaped string into the RCons.readChar buffer
| /[?]                    search for bytes, regexps, patterns, ..
| ![?] [cmd]              run given command as in system(3)
| #[?] !lang [..]         Hashbang to run an rlang script
| a[?]                    analysis commands
| b[?]                    display or change the block size
| c[?] [arg]              compare block with given data
| C[?]                    code metadata (comments, format, hints, ..)
| d[?]                    debugger commands
| e[?] [a[=b]]            list/get/set config evaluable vars
| f[?] [name][sz][at]     add flag at current address
| g[?] [arg]              generate shellcodes with r_egg
| i[?] [file]             get info about opened file from r_bin
| k[?] [sdb-query]        run sdb-query. see k? for help, 'k *', 'k **' ...
| l[?] [filepattern]      list files and directories
| L[?] [-] [plugin]       list, unload load r2 plugins
| m[?]                    mountpoints commands
| o[?] [file] ([offset])  open file at optional address
| p[?] [len]              print current block with format and length
| P[?]                    project management utilities
| q[?] [ret]              quit program with a return value
| r[?] [len]              resize file
| s[?] [addr]             seek to address (also for '0x', '0x1' == 's 0x1')
| t[?]                    types, noreturn, signatures, C parser and more
| T[?] [-] [num|msg]      Text log utility (used to chat, sync, log, ...)
| u[?]                    uname/undo seek/write
| v                       panels mode
| V                       visual mode (Vv = func/var anal, VV = graph mode, ...)
| w[?] [str]              multiple write operations
| x[?] [len]              alias for 'px' (print hexadecimal)
| y[?] [len] [[[@]addr    Yank/paste bytes from/to memory
| z[?]                    zignatures management
| ?[??][expr]             Help or evaluate math expression
| ?$?                     show available '$' variables and aliases
| ?@?                     misc help for '@' (seek), '~' (grep) (see ~?""?)
| ?>?                     output redirection
| ?|?                     help for '|' (pipe)
```

```bash
RADARE2(1)									      BSD General Commands Manual									     RADARE2(1)

NAME
     radare2 — Advanced command-line hexadecimal editor, disassembler and debugger

SYNOPSIS
     radare2 [-a arch] [-b bits] [-B baddr] [-c cmd] [-e k=v] [-i file] [-I prefile] [-k kernel] [-m addr] [-p project] [-P patch] [-r rarun2] [-R rr2rule] [-s addr] [-0AdDwntLquvVxX] -|--|=|file

DESCRIPTION
     radare2 is a command-line hexadecimal editor.

     "r2" is the alias program name for radare2.

     This manpage is not updated yet. Feel free to contribute.

     The options are:

     --		 Open radare2 on an empty file

     -		 Equivalent of 'r2 malloc://512'

     -0		 Print \x00 after initialization and after every command executed

     -2		 Close stderr before starting RCore

     -a arch	 force asm.arch (x86, ppc, arm, mips, bf, java, ...)

     -A		 run 'aaa' command before prompt or patch to analyze all referenced code. Use -AA to run aaaa

     -b bits	 force asm.bits (16, 32, 64)

     -B baddr	 Specify the base address to be used when loading a new binary. See 'e?bin.baddr'

     -c cmd	 Execute the given command before giving prompt

     -d		 Start in debugger mode

     -D dbg.backend
		 Enable debug mode. Set cfg.debug=true

     -e k=v	 Set configuration eval variable key=value. For example -e scr.color=false

     -f		 Blocksize = file size

     -i file	 Run script file. After the file is loaded

     -I file	 Run script file. Before the file is loaded

     -k kernel	 Select kernel (asm.os) for syscall resolution

     -l plugfile
		 Load given plugin file

     -L		 List supported IO plugins.

     -m addr	 map file at given address

     -M		 Disable demangling

     -n		 Do not perform any analysis (r_bin). Just load the raw file

     -nn	 Only load the rbin structures (elf, mach0, ...)

     -N		 Do not load user settings/projects from ~/.radare2rc, ~/.config/radare2/radare2rc and the scripts inside .../radare2rc.d/ directory.

     -NN	 Same as -N but also disables the automatic loading of plugins on startup time

     -q		 Quiet mode (no prompt) and quit after running the commands specified with -i or -c

     -qq	 Quit before showing the prompt. Right after all the -e -c and -i arguments are evaluated.

     -Q		 Same as q, but exiting without freeing RCore, this produces leaks at exit time, but saves some precious ms to run the testsuite in fast mode.

     -p prj	 Set project file

     -P file	 Apply rapatch file and quit (see doc/rapatch.md for more details)

     -r rarun2	 Specify dbg.profile rarun2 profile to use when spawning a program for debugging

     -R rarun2-directive
		 Specify custom rarun2 directives without having to create a rarun2 profile

     -s addr	 Start seeking at this address

     -S		 Enable sandboxed mode (same as -e cfg.sandbox=true)

     -t		 Get binary information using a thread

     -T		 Avoid computing the file hashes

     -u		 Set bin.filter=false to load rbin info without filtering names

     -v		 Show version information and exit (Use -qv to get just the version number)

     -V		 Show radare2 library versions (prints JSON format if -j is used)

     -w		 Open in write mode

     -h		 Show help message

     -H		 Show files and environment help

     -x		 Open the file map without executable permissions

     -X		 Same as -e bin.usextr=false, do not use extract plugins, useful for dyldcache

SHELL
     Type '?' for help

VISUAL
     To enter visual mode use the 'V' command. Then press '?' for help

DEBUGGER
     In r2 the debugger commands are implemented under the 'd' command. Type 'd?' for help

ENVIRONMENT
      R2_IGNVER	    load plugins ignoring the specified version. (be careful)
      R2_DEBUG	    if defined, show error messages and crash signal
      R2_DEBUG_ASSERT=1 set a breakpoint when hitting an assert
      R2_MAGICPATH /Users/pancake/.local/share/radare2/share/radare2/4.5.0-git/magic
      R2_NOPLUGINS do not load r2 shared plugins
      R2_RCFILE	   ~/.radare2rc (user preferences, batch script)
      R2_RDATAHOME /usr/local FILE path to the current working file.

SEE ALSO
     r2r(1), rahash2(1), rafind2(1), rabin2(1), radiff2(1), rasm2(1), rax2(1), ravc2(1), ragg2(1), rarun2(1),

AUTHORS
     pancake <pancake@nopcode.org>

											      May 20, 2022
```