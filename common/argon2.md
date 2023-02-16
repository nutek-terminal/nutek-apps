# argon2

## Description

Argon2 is a password-hashing function that summarizes the state of the art in the design of memory-hard functions and can be used to hash passwords for credential storage, key derivation, or other applications.

## Installation

```bash
brew install argon2
```

## Usage

```bash
echo -n "password" | argon2 somesalt -t 2 -m 16 -p 4 -l 24
```

## Resources

- [Argon2](https://github.com/P-H-C/phc-winner-argon2)

## help

```bash
Usage:  argon2 [-h] salt [-i|-d|-id] [-t iterations] [-m log2(memory in KiB) | -k memory in KiB] [-p parallelism] [-l hash length] [-e|-r] [-v (10|13)]
	Password is read from stdin
Parameters:
	salt		The salt to use, at least 8 characters
	-i		Use Argon2i (this is the default)
	-d		Use Argon2d instead of Argon2i
	-id		Use Argon2id instead of Argon2i
	-t N		Sets the number of iterations to N (default = 3)
	-m N		Sets the memory usage of 2^N KiB (default 12)
	-k N		Sets the memory usage of N KiB (default 4096)
	-p N		Sets parallelism to N threads (default 1)
	-l N		Sets hash output length to N bytes (default 32)
	-e		Output only encoded hash
	-r		Output only the raw bytes of the hash
	-v (10|13)	Argon2 version (defaults to the most recent version, currently 13)
	-h		Print argon2 usage
```