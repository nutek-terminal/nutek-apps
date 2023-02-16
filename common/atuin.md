# atuin

## Description

atuin is a blazing fast shell history tracker, written in Rust.

## Installation

```bash
brew install atuin
echo 'eval "$(atuin init zsh)"' >> ~/.zshrc
```

## Resources

- [atuin](https://github.com/ellie/atuin)

## Similar

- zsh-history-substring-search
- zsh-autosuggestions
- zsh-syntax-highlighting
- zsh-history-substring-search

## help

```bash
atuin 12.0.0
Ellie Huxtable <e@elm.sh>
Magical shell history

Usage:
  atuin <COMMAND>

Commands:
  history          Manipulate shell history
  import           Import shell history from file
  stats            Calculate statistics for your history
  search           Interactive history search
  sync             Sync with the configured server
  login            Login to the configured server
  logout           Log out
  register         Register with the configured server
  key              Print the encryption key for transfer to another machine
  server           Start an atuin server
  init             Output shell setup
  uuid             Generate a UUID
  contributors     
  gen-completions  Generate shell completions
  help             Print this message or the help of the given subcommand(s)

Options:
  -h, --help     Print help
  -V, --version  Print version
```