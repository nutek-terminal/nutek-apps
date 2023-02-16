# dust

## Description

dust is a more intuitive version of du in rust.

## Installation

```bash
brew install dust
```

## Usage

```bash
dust
```

## Resources

- [dust](https://github.com/bootandy/dust)

## help

```bash
Like du but more intuitive

USAGE:
    dust [OPTIONS] [--] [inputs]...

ARGS:
    <inputs>...    

OPTIONS:
    -b, --no-percent-bars
            No percent bars or percentages will be displayed

    -c, --no-colors
            No colors will be printed (Useful for commands like: watch)

    -d, --depth <depth>
            Depth to show

    -D, --only-dir
            Only directories will be displayed.

    -e, --filter <filter>
            Only include filepaths matching this regex. For png files type: -e "\.png$" 

    -f, --filecount
            Directory 'size' is number of child files/dirs not disk size

    -F, --only-file
            Only files will be displayed. (Finds your largest files)

    -h, --help
            Print help information

    -H, --si
            print sizes in powers of 1000 (e.g., 1.1G)

    -i, --ignore_hidden
            Do not display hidden files

    -L, --dereference-links
            dereference sym links - Treat sym links as directories and go into them

    -n, --number-of-lines <number_of_lines>
            Number of lines of output to show. (Default is terminal_height - 10)

    -p, --full-paths
            Subdirectories will not have their path shortened

    -P, --no-progress
            Disable the progress indication.

    -r, --reverse
            Print tree upside down (biggest highest)

    -R, --screen-reader
            For screen readers. Removes bars. Adds new column: depth level (May want to use -p too
            for full path)

    -s, --apparent-size
            Use file length instead of blocks

        --skip-total
            No total row will be displayed

    -t, --file_types
            show only these file types

    -v, --invert-filter <invert_filter>
            Exclude filepaths matching this regex. To ignore png files type: -v "\.png$" 

    -V, --version
            Print version information

    -w, --terminal_width <width>
            Specify width of output overriding the auto detection of terminal width

    -x, --limit-filesystem
            Only count the files and directories on the same filesystem as the supplied directory

    -X, --ignore-directory <ignore_directory>
            Exclude any file or directory with this name

    -z, --min-size <min_size>
            Minimum size file to include in output
```