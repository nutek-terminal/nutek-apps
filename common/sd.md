# sd

## Description

sd is a find and replace CLI tool that aims to be simpler and faster than other tools like sed and awk.

## Installation

```bash
brew install sd
```

## Usage

```bash
sd 'foo' 'bar' input.txt
```

## Resources

- [sd](https://github.com/chmln/sd)

## Similar

- sed
- awk

## help

```bash
sd 0.7.6

USAGE:
    sd [OPTIONS] <find> <replace-with> [files]...

OPTIONS:
    -f, --flags <flags>
            Regex flags. May be combined (like `-f mc`).
            
            c - case-sensitive
            e - disable multi-line matching
            i - case-insensitive
            m - multi-line matching
            s - make `.` match newlines
            w - match full words only
    -h, --help
            Prints help information

    -s, --string-mode
            Treat expressions as non-regex strings

    -p, --preview
            Output result into stdout and do not modify files

    -V, --version
            Prints version information


ARGS:
    <find>
            The regexp or string (if -s) to search for

    <replace-with>
            What to replace each match with. Unless in string mode, you may use captured values like $1, $2, etc

    <files>...
            The path to file(s). This is optional - sd can also read from STDIN
```