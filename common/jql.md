# jql

## Description

JQL is a command-line tool for querying JSON data. It is similar to jq, but with a more SQL-like syntax.

## install

```bash
brew install jql
```

## sample usage

```bash
jql '.' example.json
```

```json
    {
    "some": {
        "property": "value"
    }
    }
```

```
jql '"some"."property"' example.json
```

### sample output
    
```
value
```

## packege info

```
Name         : jql
Version      : 5.1.6
Release      : 1.el9
Architecture : x86_64
Size         : 1.1 M
Source       : jql-5.1.6-1.el9.src.rpm
Repository   : @System
From repo    : @commandline
Summary      : A JSON Query Language CLI tool
URL          : https://crates.io/crates/jql
License      : MIT
Description  : jql is a command line tool for querying JSON data.
             : It is inspired by jq. This tool has absolutely no plan
             : to be on par with jq and such other similar CLI.
```

## help

```
A JSON query language CLI tool

Usage: jql [OPTIONS] [selectors] [JSON]

Arguments:
  [selectors]  Selectors to apply
  [JSON]       JSON file to use

Options:
  -c, --check             Checks if the input is valid JSON
  -f, --from-file <FILE>  Reads selectors from file rather than from a command line
  -i, --inline            Inlines JSON output
  -r, --raw-output        Writes raw string selection directly to standard output without JSON double-quotes
  -s, --stream            Reads a stream of JSON data line by line
  -h, --help              Print help
  -V, --version           Print version
```