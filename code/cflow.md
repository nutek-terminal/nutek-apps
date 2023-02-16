# cflow

## Description

cflow is a program that prints a graph of the control flow of a C program.

## Installation

```bash
brew install cflow
```

## Usage

```bash
cflow [options] [file ...]
```

## Resources

- [cflow](https://www.gnu.org/software/cflow/)
- [cflow User Guide](https://www.gnu.org/software/cflow/manual/cflow.html)
- [cflow API](https://www.gnu.org/software/cflow/manual/cflow.html)

## help

```bash
CFLOW(1)										General Commands Manual										       CFLOW(1)

NAME
       cflow - generate a C-language flowgraph

SYNOPSIS
       cflow [-ASTrxablnv] [-d NUMBER] [-f NAME] [-i CLASSES] [-o FILE] [-D NAME[=DEFN]] [-I DIR] [-m NAME] [-p NUMBER] [-s SYMBOL:[=]TYPE] [-U NAME] [--all] [--depth=NUMBER] [--format=NAME]
       [--include=CLASSES] [--output=FILE] [--reverse] [--xref] [--ansi] [--define=NAME[=DEFN]] [--include-dir=DIR] [--main=NAME] [--no-main] [--pushdown=NUMBER] [--preprocess[=COMMAND]]
       [--cpp[=COMMAND]] [--symbol=SYMBOL:[=]TYPE] [--use-indentation] [--undefine=NAME] [--brief] [--emacs] [--print-level] [--level-indent=ELEMENT] [--number] [--omit-arguments]
       [--omit-symbol-names] [--tree] [--debug[=NUMBER]] [--verbose] FILE...

       cflow [-?V] [--help] [--usage] [--version]

NOTE
       This manpage is a short description of GNU cflow.  For a detailed discussion, including examples and usage recommendations, refer to the GNU Cflow Manual available in texinfo format.	If  the
       info reader and the cflow documentation are properly installed on your system, the command

	   info cflow

       should give you access to the complete manual.

       You can also view the manual using the info mode in emacs(1), or find it in various formats online at

	   http://www.gnu.org/software/cflow/manual

       If any discrepancies occur between this manpage and the GNU Cflow Manual, the later shall be considered the authoritative source.

DESCRIPTION
       Cflow analyzes a collection of input files written in C programming language and writes to standard output a graph charting dependencies between various functions.

OPTIONS
   General-purpose options
       -d, --depth=NUMBER
	      Set the depth at which the flowgraph is cut off.	By default the depth is not limited.

       --debug[=NUMBER]
	      Set debugging level.

       -f, --format=NAME
	      Use given output format NAME. Valid names are gnu (the default) and posix.

       -i, --include=CLASSES
	      Include specified classes of symbols.  The ^or- symbol excludes the classes that follow it.  Valid classes are:

	      _(underscore)
		     Symbols whose names begin with an underscore.

	      s	     Static symbols

	      t	     Typedefs (for cross-references only).

	      x	     All data symbols, both external and static

       -o, --output=FILE
	      Set output file name (default is -, meaning stdout).

       -r, --reverse
	      Print reverse call tree.

       --no-reverse
	      Disable the effect of the previous --reverse option.

       -x, --xref
	      Produce cross-reference listing only.

       -v, --verbose
	      Enable verbose error diagnostics.

   Parser control
       -a, --ansi
	      Accept only sources in ANSI C.

       --no-ansi
	      Don't assume input files are written in ANSI C.

       -D, --define=NAME[=DEFN]
	      Predefine NAME as a macro.

       -I, --include-dir=DIR
	      Add the directory DIR to the list of directories to be searched for header files.

       -m, --main=NAME
	      Assume main function is NAME

       --no-main
	      Assume there's no main function in the program.  This option has the same effect as --all, except that, if the program do define the main function, it will be treated as any other func‐
	      tions, i.e. it will not be placed at the top of output, but in its place as per the lexicographic ordering of function names.  See also the description of --all.

       -p, --pushdown=NUMBER
	      Set initial token stack size to NUMBER.

       --preprocess[=COMMAND], --cpp[=COMMAND]
	      Run the specified preprocessor command.

       --no-preprocess, --no-cpp
	      Disable preprocessing.

       -s, --symbol=SYMBOL:[=]TYPE
	      Register SYMBOL with given TYPE, or define an alias (if := is used). Valid types are: keyword(orkw), modifier, qualifier, identifier, type, and wrapper.	Any unambiguous abbreviation of
	      the above is also accepted.

       -S, --use-indentation
	      Rely on indentation to solve suspicious constructs.

       --no-use-indentation
	      Don't use indentation in parsing (default).

       -U, --undefine=NAME
	      Cancel any previous definition of NAME.

   Output control
       -A, --all
	      Produce graphs for all global functions in the program.  Use this option if your program contains functions which are not directly reachable from main().

	      The  output  consist  of separate flow graphs for each top-level function defined in the program.	 These graphs will be placed after the graph for main() (if it exists), and will be or‐
	      dered lexicographically by the function name.

	      If used twice, graphs for all global functions (whether top-level or not) will be displayed.

       -b, --brief
	      Brief output.

       --no-brief
	      Disable brief output.

       --emacs
	      Format output for use with GNU Emacs.

       --no-emacs
	      Disable the effect of the previous --emacs option.

       -l, --print-level
	      Print nesting level along with the call tree.

       --no-print-level
	      Don't print nesting level.

       --level-indent=ELEMENT
	      Control graph appearance.

       -n, --number
	      Print line numbers.

       --no-number
	      Don't print line numbers.

       --omit-arguments
	      Do not print argument lists in function declarations.

       --no-omit-arguments
	      Print argument lists in function declarations (the default).

       --omit-symbol-names
	      Do not print symbol names in declaration strings.

       --no-omit-symbol-names
	      Print symbol names in declaration strings (the default).

       -T, --tree
	      Draw ASCII art tree.

       --no-tree
	      Disable tree output.

   Informational options
       These options instruct the program to output the requested piece of information and exit.

       -?, --help
	      Print a short help summary.

       --usage
	      Print a summary of available options.

       -V, --version
	      Print program version.

RETURN VALUE
       0      Successful completion.

       1      Fatal error occurred.

       2      Some input files cannot be read or parsed.

       3      Command line usage error.

SEE ALSO
       Online copies of GNU cflow documentation in various formats can be found at:

	   http://www.gnu.org/software/cflow/manual

AUTHORS
       Sergey Poznyakoff

BUG REPORTS
       Report bugs to <bug-cflow@gnu.org>.

COPYRIGHT
       Copyright © 2014-2021 Sergey Poznyakoff
       License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
       This is free software: you are free to change and redistribute it.  There is NO WARRANTY, to the extent permitted by law.

CFLOW											   February 10, 2019										       CFLOW(1)
```