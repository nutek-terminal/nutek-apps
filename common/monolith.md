# monolith

## Description

monolith is a command-line tool that converts web pages to plain text or PDF.

## Installation

```bash
brew install monolith
```

## Usage

```bash
monolith https://example.com
```

## Resources

- [monolith](https://github.com/Y2Z/monolith)

## help

```bash
monolith 2.7.0

Sunshine <sunshine@uberspace.net>
Mahdi Robatipoor <mahdi.robatipoor@gmail.com>
Emmanuel Delaborde <th3rac25@gmail.com>
Emi Simpson <emi@alchemi.dev>
rhysd <lin90162@yahoo.co.jp>

 _____     ______________    __________      ___________________    ___
|     \   /              \  |          |    |                   |  |   |
|      \_/       __       \_|    __    |    |    ___     ___    |__|   |
|               |  |            |  |   |    |   |   |   |   |          |
|   |\     /|   |__|    _       |__|   |____|   |   |   |   |    __    |
|   | \___/ |          | \                      |   |   |   |   |  |   |
|___|       |__________|  \_____________________|   |___|   |___|  |___|

CLI tool for saving web pages as a single HTML file

USAGE:
    monolith [OPTIONS] <target>

ARGS:
    <target>    URL or file path, use - for STDIN

OPTIONS:
    -a, --no-audio                        Removes audio sources
    -b, --base-url <http://localhost/>    Sets custom base URL
    -B, --blacklist-domains               Treat list of specified domains as blacklist
    -c, --no-css                          Removes CSS
    -C, --charset <UTF-8>                 Enforces custom encoding
    -d, --domain <example.com>            Specify domains to use for white/black-listing
    -e, --ignore-errors                   Ignore network errors
    -f, --no-frames                       Removes frames and iframes
    -F, --no-fonts                        Removes fonts
    -h, --help                            Print help information
    -i, --no-images                       Removes images
    -I, --isolate                         Cuts off document from the Internet
    -j, --no-js                           Removes JavaScript
    -k, --insecure                        Allows invalid X.509 (TLS) certificates
    -M, --no-metadata                     Excludes timestamp and source information
    -n, --unwrap-noscript                 Replaces NOSCRIPT elements with their contents
    -o, --output <document.html>          Writes output to <file>, use - for STDOUT
    -s, --silent                          Suppresses verbosity
    -t, --timeout <60>                    Adjusts network request timeout
    -u, --user-agent <Firefox>            Sets custom User-Agent string
    -v, --no-video                        Removes video sources
    -V, --version                         Print version information
```