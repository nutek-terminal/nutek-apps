# nutek-apps

Apps inside Nutek Terminal with their respective usage and other important
information. Working on macOS & Linux (different way of installation [maybe dnf]).

## Wordlists

* [SecLists](https://github.com/danielmiessler/SecLists)
* [Assetnote](https://wordlists.assetnote.io/)
* [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)
* [Payloads](https://github.com/sh377c0d3/Payloads)

## Tools for my workflow

Install with brew:
    
```bash
# Install brew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
# Install all apps
bash <(curl -s https://raw.githubusercontent.com/nutek-terminal/nutek-apps/main/brew_install_list.sh)
```

## Trick for manpages

```
man tcpflow | col -b > manpage.txt
```
