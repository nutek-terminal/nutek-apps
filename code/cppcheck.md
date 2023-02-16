# cppcheck

## Description

Cppcheck is a static analysis tool for C/C++ code.

## Installation

```bash
brew install cppcheck
```

## Usage

```bash
cppcheck hello.cpp
```

## Resources

- [Cppcheck](http://cppcheck.sourceforge.net/)
- [Cppcheck User Guide](http://cppcheck.sourceforge.net/manual.pdf)
- [Cppcheck API](http://cppcheck.sourceforge.net/api/index.html)

## help

```bash
Cppcheck - A tool for static C/C++ code analysis

Syntax:
    cppcheck [OPTIONS] [files or paths]

If a directory is given instead of a filename, *.cpp, *.cxx, *.cc, *.c++, *.c, *.ipp,
*.ixx, *.tpp, and *.txx files are checked recursively from the given directory.

Options:
    --addon=<addon>
                         Execute addon. i.e. --addon=misra. If options must be
                         provided a json configuration is needed.
    --addon-python=<python interpreter>
                         You can specify the python interpreter either in the
                         addon json files or through this command line option.
                         If not present, Cppcheck will try "python3" first and
                         then "python".
    --cppcheck-build-dir=<dir>
                         Cppcheck work folder. Advantages:
                          * whole program analysis
                          * faster analysis; Cppcheck will reuse the results if
                            the hash for a file is unchanged.
                          * some useful debug information, i.e. commands used to
                            execute clang/clang-tidy/addons.
    --check-config       Check cppcheck configuration. The normal code
                         analysis is disabled by this flag.
    --check-library      Show information messages when library files have
                         incomplete info.
    --clang=<path>       Experimental: Use Clang parser instead of the builtin Cppcheck
                         parser. Takes the executable as optional parameter and
                         defaults to `clang`. Cppcheck will run the given Clang
                         executable, import the Clang AST and convert it into
                         Cppcheck data. After that the normal Cppcheck analysis is
                         used. You must have the executable in PATH if no path is
                         given.
    --config-exclude=<dir>
                         Path (prefix) to be excluded from configuration
                         checking. Preprocessor configurations defined in
                         headers (but not sources) matching the prefix will not
                         be considered for evaluation.
    --config-excludes-file=<file>
                         A file that contains a list of config-excludes
    --dump               Dump xml data for each translation unit. The dump
                         files have the extension .dump and contain ast,
                         tokenlist, symboldatabase, valueflow.
    -D<ID>               Define preprocessor symbol. Unless --max-configs or
                         --force is used, Cppcheck will only check the given
                         configuration when -D is used.
                         Example: '-DDEBUG=1 -D__cplusplus'.
    -E                   Print preprocessor output on stdout and don't do any
                         further processing.
    --enable=<id>        Enable additional checks. The available ids are:
                          * all
                                  Enable all checks. It is recommended to only
                                  use --enable=all when the whole program is
                                  scanned, because this enables unusedFunction.
                          * warning
                                  Enable warning messages
                          * style
                                  Enable all coding style checks. All messages
                                  with the severities 'style', 'warning',
                                  'performance' and 'portability' are enabled.
                          * performance
                                  Enable performance messages
                          * portability
                                  Enable portability messages
                          * information
                                  Enable information messages
                          * unusedFunction
                                  Check for unused functions. It is recommended
                                  to only enable this when the whole program is
                                  scanned.
                          * missingInclude
                                  Warn if there are missing includes. For
                                  detailed information, use '--check-config'.
                         Several ids can be given if you separate them with
                         commas. See also --std
    --error-exitcode=<n> If errors are found, integer [n] is returned instead of
                         the default '0'. '1' is returned
                         if arguments are not valid or if no input files are
                         provided. Note that your operating system can modify
                         this value, e.g. '256' can become '0'.
    --errorlist          Print a list of all the error messages in XML format.
    --exitcode-suppressions=<file>
                         Used when certain messages should be displayed but
                         should not cause a non-zero exitcode.
    --file-filter=<str>  Analyze only those files matching the given filter str
                         Can be used multiple times
                         Example: --file-filter=*bar.cpp analyzes only files
                                  that end with bar.cpp.
    --file-list=<file>   Specify the files to check in a text file. Add one
                         filename per line. When file is '-,' the file list will
                         be read from standard input.
    -f, --force          Force checking of all configurations in files. If used
                         together with '--max-configs=', the last option is the
                         one that is effective.
    -h, --help           Print this help.
    -I <dir>             Give path to search for include files. Give several -I
                         parameters to give several paths. First given path is
                         searched for contained header files first. If paths are
                         relative to source files, this is not needed.
    --includes-file=<file>
                         Specify directory paths to search for included header
                         files in a text file. Add one include path per line.
                         First given path is searched for contained header
                         files first. If paths are relative to source files,
                         this is not needed.
    --include=<file>
                         Force inclusion of a file before the checked file.
    -i <dir or file>     Give a source file or source file directory to exclude
                         from the check. This applies only to source files so
                         header files included by source files are not matched.
                         Directory name is matched to all parts of the path.
    --inconclusive       Allow that Cppcheck reports even though the analysis is
                         inconclusive.
                         There are false positives with this option. Each result
                         must be carefully investigated before you know if it is
                         good or bad.
    --inline-suppr       Enable inline suppressions. Use them by placing one or
                         more comments, like: '// cppcheck-suppress warningId'
                         on the lines before the warning to suppress.
    -j <jobs>            Start <jobs> threads to do the checking simultaneously.
    -l <load>            Specifies that no new threads should be started if
                         there are other threads running and the load average is
                         at least <load>.
    --language=<language>, -x <language>
                         Forces cppcheck to check all files as the given
                         language. Valid values are: c, c++
    --library=<cfg>      Load file <cfg> that contains information about types
                         and functions. With such information Cppcheck
                         understands your code better and therefore you
                         get better results. The std.cfg file that is
                         distributed with Cppcheck is loaded automatically.
                         For more information about library files, read the
                         manual.
    --max-configs=<limit>
                         Maximum number of configurations to check in a file
                         before skipping it. Default is '12'. If used together
                         with '--force', the last option is the one that is
                         effective.
    --max-ctu-depth=N    Max depth in whole program analysis. The default value
                         is 2. A larger value will mean more errors can be found
                         but also means the analysis will be slower.
    --output-file=<file> Write results to file, rather than standard error.
    --platform=<type>, --platform=<file>
                         Specifies platform specific types and sizes. The
                         available builtin platforms are:
                          * unix32
                                 32 bit unix variant
                          * unix64
                                 64 bit unix variant
                          * win32A
                                 32 bit Windows ASCII character encoding
                          * win32W
                                 32 bit Windows UNICODE character encoding
                          * win64
                                 64 bit Windows
                          * avr8
                                 8 bit AVR microcontrollers
                          * elbrus-e1cp
                                 Elbrus e1c+ architecture
                          * pic8
                                 8 bit PIC microcontrollers
                                 Baseline and mid-range architectures
                          * pic8-enhanced
                                 8 bit PIC microcontrollers
                                 Enhanced mid-range and high end (PIC18) architectures
                          * pic16
                                 16 bit PIC microcontrollers
                          * mips32
                                 32 bit MIPS microcontrollers
                          * native
                                 Type sizes of host system are assumed, but no
                                 further assumptions.
                          * unspecified
                                 Unknown type sizes
    --plist-output=<path>
                         Generate Clang-plist output files in folder.
    --project=<file>     Run Cppcheck on project. The <file> can be a Visual
                         Studio Solution (*.sln), Visual Studio Project
                         (*.vcxproj), compile database (compile_commands.json),
                         or Borland C++ Builder 6 (*.bpr). The files to analyse,
                         include paths, defines, platform and undefines in
                         the specified file will be used.
    --project-configuration=<config>
                         If used together with a Visual Studio Solution (*.sln)
                         or Visual Studio Project (*.vcxproj) you can limit
                         the configuration cppcheck should check.
                         For example: '--project-configuration=Release|Win32'
    -q, --quiet          Do not show progress reports.
    -rp=<paths>, --relative-paths=<paths>
                         Use relative paths in output. When given, <paths> are
                         used as base. You can separate multiple paths by ';'.
                         Otherwise path where source files are searched is used.
                         We use string comparison to create relative paths, so
                         using e.g. ~ for home folder does not work. It is
                         currently only possible to apply the base paths to
                         files that are on a lower level in the directory tree.
    --report-progress    Report progress messages while checking a file.
    --rule=<rule>        Match regular expression.
    --rule-file=<file>   Use given rule file. For more information, see:
                         http://sourceforge.net/projects/cppcheck/files/Articles/
    --std=<id>           Set standard.
                         The available options are:
                          * c89
                                 C code is C89 compatible
                          * c99
                                 C code is C99 compatible
                          * c11
                                 C code is C11 compatible (default)
                          * c++03
                                 C++ code is C++03 compatible
                          * c++11
                                 C++ code is C++11 compatible
                          * c++14
                                 C++ code is C++14 compatible
                          * c++17
                                 C++ code is C++17 compatible
                          * c++20
                                 C++ code is C++20 compatible (default)
    --suppress=<spec>    Suppress warnings that match <spec>. The format of
                         <spec> is:
                         [error id]:[filename]:[line]
                         The [filename] and [line] are optional. If [error id]
                         is a wildcard '*', all error ids match.
    --suppressions-list=<file>
                         Suppress warnings listed in the file. Each suppression
                         is in the same format as <spec> above.
    --suppress-xml=<file>
                         Suppress warnings listed in a xml file. XML file should
                         follow the manual.pdf format specified in section.
                         `6.4 XML suppressions` .
    --template='<text>'  Format the error messages. Available fields:
                           {file}              file name
                           {line}              line number
                           {column}            column number
                           {callstack}         show a callstack. Example:
                                                 [file.c:1] -> [file.c:100]
                           {inconclusive:text} if warning is inconclusive, text
                                               is written
                           {severity}          severity
                           {message}           warning message
                           {id}                warning id
                           {cwe}               CWE id (Common Weakness Enumeration)
                           {code}              show the real code
                           \t                 insert tab
                           \n                 insert newline
                           \r                 insert carriage return
                         Example formats:
                         '{file}:{line},{severity},{id},{message}' or
                         '{file}({line}):({severity}) {message}' or
                         '{callstack} {message}'
                         Pre-defined templates: gcc (default), cppcheck1 (old default), vs, edit.
    --template-location='<text>'
                         Format error message location. If this is not provided
                         then no extra location info is shown.
                         Available fields:
                           {file}      file name
                           {line}      line number
                           {column}    column number
                           {info}      location info
                           {code}      show the real code
                           \t         insert tab
                           \n         insert newline
                           \r         insert carriage return
                         Example format (gcc-like):
                         '{file}:{line}:{column}: note: {info}\n{code}'
    -U<ID>               Undefine preprocessor symbol. Use -U to explicitly
                         hide certain #ifdef <ID> code paths from checking.
                         Example: '-UDEBUG'
    -v, --verbose        Output more detailed error information.
    --version            Print out version number.
    --xml                Write results in xml format to error stream (stderr).

Example usage:
  # Recursively check the current folder. Print the progress on the screen and
  # write errors to a file:
  cppcheck . 2> err.txt

  # Recursively check ../myproject/ and don't print progress:
  cppcheck --quiet ../myproject/

  # Check test.cpp, enable all checks:
  cppcheck --enable=all --inconclusive --library=posix test.cpp

  # Check f.cpp and search include files from inc1/ and inc2/:
  cppcheck -I inc1/ -I inc2/ f.cpp

For more information:
    https://cppcheck.sourceforge.io/manual.pdf

Many thanks to the 3rd party libraries we use:
 * tinyxml2 -- loading project/library/ctu files.
 * picojson -- loading compile database.
 * pcre -- rules.
 * qt -- used in GUI
```

```bash
CPPCHECK(1)										  cppcheck User Manual										    CPPCHECK(1)

NAME
       cppcheck - Tool for static C/C++ code analysis

SYNOPSIS
       cppcheck [--check-config] [--check-library] [-D<id>] [-U<id>] [--enable=<id>] [--error-exitcode=<n>] [--errorlist] [--exitcode-suppressions=<file>] [--file-list=<file>] [--force] [--help]
		[-I<dir>] [--includes-file=<file>] [--config-exclude=<dir>] [--config-excludes-file=<file>] [--include=<file>] [-i<dir>] [--inconclusive] [--inline-suppr] [-j<jobs>] [-l<load>]
		[--language=<language>] [--library=<cfg>] [--max-configs=<limit>] [--max-ctu-depth=<limit>] [--platform=<type>] [--quiet] [--relative-paths=<paths>] [--report-progress]
		[--rule=<rule>] [--rule-file=<file>] [--std=<id>] [--suppress=<spec>] [--suppressions-list=<file>] [--suppress-xml=<.xml file>] [--template='<text>'] [--verbose] [--version] [--xml]
		[--xml-version=<version>]] [file or path] ...

DESCRIPTION
       Cppcheck is a command-line tool that tries to detect bugs that your C/C++ compiler doesn't see. It is versatile, and can check non-standard code including various compiler extensions, inline
       assembly code, etc. Its internal preprocessor can handle includes, macros, and several preprocessor commands. While Cppcheck is highly configurable, you can start using it just by giving it a
       path to the source code.

OPTIONS
       Analyze given C/C++ files for common errors.

       --check-config
	   Check Cppcheck configuration. The normal code analysis is disabled by this flag.

       --check-library
	   Show information messages when library files have incomplete info.

       -D<id>
	   By default Cppcheck checks all configurations. Use -D to limit the checking. When -D is used the checking is limited to the given configuration. Example: -DDEBUG=1 -D__cplusplus

       -U<id>
	   By default Cppcheck checks all configurations. Use '-U' to explicitly hide certain #ifdef <id> code paths from checking. Example: '-UDEBUG'

       --enable=<id>
	   Enable additional checks. The available ids are:

	   all
	       Enable all checks. It is recommended to only use --enable=all when the whole program is scanned, because this enables unusedFunction.

	   warning
	       Enable warning messages

	   style
	       Enable all coding style checks. All messages with the severities 'style', 'performance' and 'portability' are enabled.

	   performance
	       Enable performance messages

	   portability
	       Enable portability messages

	   information
	       Enable information messages

	   unusedFunction
	       Check for unused functions. It is recommend to only enable this when the whole program is scanned

	   missingInclude
	       Warn if there are missing includes. For detailed information use --check-config

	   By default none of the additional checks are enabled. Several ids can be given if you separate them with commas, e.g. --enable=style,unusedFunction. See also --std

       --error-exitcode=<n>
	   If errors are found, integer <n> is returned instead of default 0. EXIT_FAILURE is returned if arguments are not valid or if no input files are provided. Note that your operating system
	   can modify this value, e.g. 256 can become 0.

       --errorlist
	   Print a list of all possible error messages in XML format.

       --exitcode-suppressions=<file>
	   Used when certain messages should be displayed but should not cause a non-zero exitcode.

       --file-list=<file>
	   Specify the files to check in a text file. One filename per line. When file is -, the file list will be read from standard input.

       -f, --force
	   Force checking of files that have a lot of configurations. Error is printed if such a file is found so there is no reason to use this by default. If used together with --max-configs=, the
	   last option is the one that is effective.

       -h, --help
	   Print help text.

       -I <dir>
	   Give path to search for include files. Give several -I parameters to give several paths. First given path is searched for contained header files first. If paths are relative to source
	   files, this is not needed.

       --includes-file=<file>
	   Specify directory paths to search for included header files in a text file. Add one include path per line. First given path is searched for contained header files first. If paths are
	   relative to source files, this is not needed.

       --config-exclude=<dir>
	   Path (prefix) to be excluded from configuration checking. Preprocessor configurations defined in headers (but not sources) matching the prefix will not be considered for evaluation of
	   configuration alternatives.

       --config-exclude-file=<file>
	   A file that contains a list of config-excludes.

       --include=<file>
	   Force inclusion of a file before the checked file. Can be used for example when checking the Linux kernel, where autoconf.h needs to be included for every file compiled. Works the same way
	   as the GCC -include option.

       -i <dir>
	   Give path to ignore. Give several -i parameters to ignore several paths. Give directory name or filename with path as parameter. Directory name is matched to all parts of the path.

       --inconclusive
	   Allow that Cppcheck reports even though the analysis is inconclusive. There are false positives with this option. Each result must be carefully investigated before you know if it is good
	   or bad.

       --inline-suppr
	   Enable inline suppressions. Use them by placing comments in the form: // cppcheck-suppress memleak before the line to suppress.

       -j <jobs>
	   Start <jobs> threads to do the checking work.

       -l <load>
	   Specifies that no new threads should be started if there are other threads running and the load average is at least <load> (ignored on non UNIX-like systems)

       --language=<language>
	   Forces cppcheck to check all files as the given language. Valid values are: c, c++

       --library=<cfg>
	   Use library configuration.

       --max-configs=<limit>
	   Maximum number of configurations to check in a file before skipping it. Default is 12. If used together with --force, the last option is the one that is effective.

       --max-ctu-depth=<limit>
	   Maximum depth in whole program analysis. Default is 2.

       --platform=<type>
	   Specifies platform specific types and sizes.The available platforms are:

	   unix32
	       32 bit unix variant

	   unix64
	       64 bit unix variant

	   win32A
	       32 bit Windows ASCII character encoding

	   win32W
	       32 bit Windows UNICODE character encoding

	   win64
	       64 bit Windows

	   By default the platform which was used to compile Cppcheck is used.

       -q, --quiet
	   Only print something when there is an error.

       -rp, -rp=<paths>, --relative-paths;, --relative-paths=<paths>
	   Use relative paths in output. When given, <paths> are used as base. You can separate multiple paths by ';'. Otherwise path where source files are searched is used. E.g. if given value is
	   test, when checking test/test.cpp, the path in output will be test.cpp instead of test/test.cpp. The feature uses string comparison to create relative paths, so using e.g. ~ for home
	   folder does not work. It is currently only possible to apply the base paths to files that are on a lower level in the directory tree.

       --report-progress
	   Report progress when checking a file.

       --rule=<rule>
	   Match regular expression to create your own checks. E.g. rule "/ 0" can be used to check division by zero. This command is only available if cppcheck was compiled with HAVE_RULES=yes.

       --rule-file=<file>
	   Use given rule XML file. See https://sourceforge.net/projects/cppcheck/files/Articles/ for more info about the syntax. This command is only available if cppcheck was compiled with
	   HAVE_RULES=yes.

       --std=<id>
	   Set standard. The available options are:

	   c89
	       C code is C89 compatible

	   c99
	       C code is C99 compatible

	   c11
	       C code is C11 compatible (default)

	   c++03
	       C++ code is C++03 compatible

	   c++11
	       C++ code is C++11 compatible (default)

       --suppress=<spec>
	   Suppress a specific warning. The format of <spec> is: [error id]:[filename]:[line]. The [filename] and [line] are optional. [error id] may be * to suppress all warnings (for a specified
	   file or files). [filename] may contain the wildcard characters * or ?.

       --suppressions-list=<file>
	   Suppress warnings listed in the file. Each suppression is in the format of <spec> above.

       --suppress-xml=<.xml file>
	   Use suppressions defined in xml as described in the manual

       --template='<text>'
	   Format the error messages. E.g. '{file}:{line},{severity},{id},{message}' or '{file}({line}):({severity}) {message}'. Pre-defined templates: gcc, vs

       -v, --verbose
	   More detailed error reports

       --version
	   Print out version information

       --xml
	   Write results in XML to error stream

       --xml-version=<version>
	   Select the XML file version. Also implies --xml. Currently only version 2 is available. The default version is 2.

AUTHOR
       The program was written by Daniel Marjamäki and Cppcheck team. See AUTHORS file for list of team members.

SEE ALSO
       Full list of features: https://sourceforge.net/p/cppcheck/wiki/Home/

AUTHOR
       Reijo Tomperi <aggro80@users.sourceforge.net>
	   Wrote this manpage for the Debian system.

COPYRIGHT
       Copyright © 2009 - 2016 Reijo Tomperi

       This manual page was written for the Debian system (but may be used by others).

       Permission is granted to copy, distribute and/or modify this document under the terms of the GNU General Public License, Version 3 or (at your option) any later version published by the Free
       Software Foundation.

       On Debian systems, the complete text of the GNU General Public License can be found in /usr/share/common-licenses/GPL-3.

cppcheck										       08/28/2022										    CPPCHECK(1)
```