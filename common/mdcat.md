# mdcat

## Description

mdcat is a command-line tool that renders markdown files to the terminal.

## Installation

```bash
brew install mdcat
```

## Usage

```bash
mdcat README.md
```

## Resources

- [mdcat](https://github.com/swsnr/mdcat)

## help

```bash
cat for markdown: Show markdown documents in terminals

Usage: mdcat [OPTIONS] [FILENAMES]...

Arguments:
  [FILENAMES]...  Files to read.  If - read from standard input instead [default: -]

Options:
  -c, --no-colour          Disable all colours and other styles
      --columns <COLUMNS>  Maximum number of columns to use for output
  -l, --local              Do not load remote resources like images
      --fail               Exit immediately if any error occurs processing an input file
      --detect-terminal    Print detected terminal name and exit
      --ansi               Skip terminal detection and only use ANSI formatting
  -p, --paginate           Paginate the output of mdcat with a pager like less
  -P, --no-pager           Do not paginate output (default). Overrides an earlier --paginate
  -h, --help               Print help
  -V, --version            Print version

See 'man 1 mdcat' for more information.

Report issues to <https://github.com/swsnr/mdcat>.
```