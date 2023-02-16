# john

## Description

John the Ripper is a fast password cracker, currently available for many flavors of Unix, Windows, DOS, BeOS, and OpenVMS. Its primary purpose is to detect weak Unix passwords. Besides several crypt(3) password hash types most commonly found on various Unix flavors, supported out of the box are Windows LM hashes, plus lots of other hashes and ciphers in the community-enhanced version.

## install

```bash
brew install john
```

## sample usage

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt --format=raw-md5 hash.txt
```

## website

[https://www.openwall.com/john/](https://www.openwall.com/john/)

## help

[https://www.openwall.com/john/doc/](https://www.openwall.com/john/doc/)

```bash
John the Ripper password cracker, version 1.8.0
Copyright (c) 1996-2013 by Solar Designer
Homepage: http://www.openwall.com/john/

Usage: john [OPTIONS] [PASSWORD-FILES]
--single                   "single crack" mode
--wordlist=FILE --stdin    wordlist mode, read words from FILE or stdin
--rules                    enable word mangling rules for wordlist mode
--incremental[=MODE]       "incremental" mode [using section MODE]
--external=MODE            external mode or word filter
--stdout[=LENGTH]          just output candidate passwords [cut at LENGTH]
--restore[=NAME]           restore an interrupted session [called NAME]
--session=NAME             give a new session the NAME
--status[=NAME]            print status of a session [called NAME]
--make-charset=FILE        make a charset, FILE will be overwritten
--show                     show cracked passwords
--test[=TIME]              run tests and benchmarks for TIME seconds each
--users=[-]LOGIN|UID[,..]  [do not] load this (these) user(s) only
--groups=[-]GID[,..]       load users [not] of this (these) group(s) only
--shells=[-]SHELL[,..]     load users with[out] this (these) shell(s) only
--salts=[-]N               load salts with[out] at least N passwords only
--save-memory=LEVEL        enable memory saving, at LEVEL 1..3
--node=MIN[-MAX]/TOTAL     this node's number range out of TOTAL count
--fork=N                   fork N processes
--format=NAME              force hash type NAME: descrypt/bsdicrypt/md5crypt/
                           bcrypt/LM/AFS/tripcode/dummy/crypt
```