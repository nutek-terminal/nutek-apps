# viu

## Description

viu is a command-line image viewer for the terminal.

## Installation

```bash
brew install viu
```

## Usage

```bash
viu image.png
```

## Resources

- [viu](https://github.com/atanunq/viu)

## Similar

- imgcat
- img2txt
- catimg
- tiv
- jp2a
- caca-utils
- w3m
- ueberzug
- kitty
- iterm2

## help

```bash
viu 1.4.0
Atanas Yankov <atanas.yankov98@gmail.com>
View images right from the terminal.

USAGE:
    viu [FLAGS] [OPTIONS] [FILE]...
    When FILE is -, read standard input.

FLAGS:
    -b, --blocks         Force block output
        --help           Prints help information
    -m, --mirror         Display a mirror of the original image
    -n, --name           Output the name of the file before displaying
    -1, --once           Only loop once through the animation
    -r, --recursive      Recurse down directories if passed one
    -s, --static         Show only first frame of gif
    -t, --transparent    Display transparent image with transparent background
    -V, --version        Prints version information

OPTIONS:
    -f, --frame-rate <frames-per-second>    Play gif at the given frame rate
    -h, --height <height>                   Resize the image to a provided height
    -w, --width <width>                     Resize the image to a provided width

ARGS:
    <FILE>...    The image to be displayed
```