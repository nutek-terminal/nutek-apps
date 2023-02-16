# hexyl

## Description

hexyl is a command-line hex viewer.

## Installation

```bash
brew install hexyl
```

## Usage

```bash
hexyl file
```

## Resources

- [hexyl](https://github.com/sharkdp/hexyl)

## help

```bash
hexyl 0.10.0
A command-line hex viewer

USAGE:
    hexyl [OPTIONS] [FILE]

ARGS:
    <FILE>    The file to display. If no FILE argument is given, read from STDIN.

OPTIONS:
    -n, --length <N>            Only read N bytes from the input. The N argument can also
                                include a unit with a decimal prefix (kB, MB, ..) or
                                binary prefix (kiB, MiB, ..), or can be specified using a
                                hex number. The short option '-l' can be used as an alias.
                                Examples: --length=64, --length=4KiB, --length=0xff
    -c, --bytes <N>             An alias for -n/--length
    -s, --skip <N>              Skip the first N bytes of the input. The N argument can
                                also include a unit (see `--length` for details)
                                A negative value is valid and will seek from the end of
                                the file.
        --block-size <SIZE>     Sets the size of the `block` unit to SIZE (default is
                                512).
                                Examples: --block-size=1024, --block-size=4kB
    -v, --no-squeezing          Displays all input data. Otherwise any number of groups of
                                output lines which would be identical to the preceding
                                group of lines, are replaced with a line comprised of a
                                single asterisk.
        --color <WHEN>          When to use colors. The auto-mode only displays colors if
                                the output goes to an interactive terminal [default:
                                always] [possible values: always, auto, never]
    -p, --plain                 Display output with --no-characters, --no-position,
                                --border=none, and --color=never.
        --border <STYLE>        Whether to draw a border with Unicode characters, ASCII
                                characters, or none at all [default: unicode] [possible
                                values: unicode, ascii, none]
    -C, --no-characters         Whether to display the character panel on the right.
    -P, --no-position           Whether to display the position panel on the left.
    -o, --display-offset <N>    Add N bytes to the displayed file position. The N argument
                                can also include a unit (see `--length` for details)
                                A negative value is valid and calculates an offset
                                relative to the end of the file.
    -h, --help                  Print help information
    -V, --version               Print version information
```