# macchina

## Description

macchina is a minimal, cross-platform system information tool written in Rust.

## Installation

```bash
brew install macchina
```

## Usage

```bash
macchina
```

## Resources

- [macchina](https://github.com/Macchina-CLI/macchina)

## help

```bash
Usage: macchina [OPTIONS]

Options:
  -v, --version                Prints version information
  -o, --show <SHOW>            Displays only the specified readouts
  -d, --doctor                 Checks the system for failures
  -U, --long-uptime            Lengthens uptime output
  -S, --long-shell             Lengthens shell output
  -K, --long-kernel            Lengthens kernel output
  -C, --physical-cores         Toggles between logical and physical cores
  -s, --current-shell          Toggles between the current shell and the default one
  -t, --theme <THEME>          Specify the name of the theme
  -l, --list-themes            Lists all available themes: built-in and custom
  -c, --config <CONFIG>        Specify a custom path for the configuration file
      --ascii-artists          Lists the original artists of the ASCII art used by macchina
  -i, --interface <INTERFACE>  Specify the network interface for the LocalIP readout
  -h, --help                   Print help
```