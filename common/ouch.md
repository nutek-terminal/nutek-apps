# ouch

## Description

ouch is a command-line tool to apply operations on files.

## Installation

```bash
brew install ouch
```

## Usage

```bash
ouch d foo.tar.gz
```

## Resources

- [ouch](https://github.com/ouch-org/ouch)

## Similar

- tar
- unzip
- unrar
- 7z
- xz
- bzip2
- gzip
- zip
- p7zip

## help

```bash
A command-line utility for easily compressing and decompressing files and directories.

Supported formats: tar, zip, bz/bz2, gz, lz4, xz/lz/lzma, zst.

Repository: https://github.com/ouch-org/ouch

Usage: ouch [OPTIONS] <COMMAND>

Commands:
  compress
          Compress one or more files into one output file [aliases: c]
  decompress
          Decompresses one or more files, optionally into another folder [aliases: d]
  list
          List contents of an archive [aliases: l]
  help
          Print this message or the help of the given subcommand(s)

Options:
  -y, --yes
          Skip [Y/n] questions positively

  -n, --no
          Skip [Y/n] questions negatively

  -A, --accessible
          Activate accessibility mode, reducing visual noise
          
          [env: ACCESSIBLE=]

  -H, --hidden
          Ignores hidden files

  -q, --quiet
          Silences output

  -g, --gitignore
          Ignores files matched by git's ignore files

  -h, --help
          Print help (see a summary with '-h')

  -V, --version
          Print version
```