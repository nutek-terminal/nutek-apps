# xh

## Description

xh is a command-line HTTP client. It is a wrapper around the [reqwest](

## Installation

```bash
brew install xh
```

## Examples

### GET

```bash
xh https://httpbin.org/get
```

### POST

```bash
xh POST https://httpbin.org/post < file.json
```

### POST with JSON

```bash
xh POST https://httpbin.org/post < file.json
```

### POST with form data

```bash
xh POST https://httpbin.org/post foo=bar baz=quux
```

### POST with form data and JSON

```bash
xh POST https://httpbin.org/post foo=bar baz=quux < file.json
```

### POST with form data and JSON, and a header

```bash
xh POST https://httpbin.org/post foo=bar baz=quux < file.json -h "X-Foo: bar"
```

### POST with form data and JSON, and multiple headers

```bash
xh POST https://httpbin.org/post foo=bar baz=quux < file.json -h "X-Foo: bar" -h "X-Baz: quux"
```

### POST with form data and JSON, and multiple headers, and a cookie

```bash
xh POST https://httpbin.org/post foo=bar baz=quux < file.json -h "X-Foo: bar" -h "X-Baz: quux" -c "foo=bar; baz=quux"
```

### POST with form data and JSON, and multiple headers, and multiple cookies

```bash
xh POST https://httpbin.org/post foo=bar baz=quux < file.json -h "X-Foo: bar" -h "X-Baz: quux" -c "foo=bar; baz=quux" -c "foo=bar; baz=quux"
```

### POST with form data and JSON, and multiple headers, and multiple cookies, and a basic auth

```bash
xh POST https://httpbin.org/post foo=bar baz=quux < file.json -h "X-Foo: bar" -h "X-Baz: quux" -c "foo=bar; baz=quux" -c "foo=bar; baz=quux" -a "foo:bar"
```

### POST with form data and JSON, and multiple headers, and multiple cookies, and a basic auth, and a timeout

```bash
xh POST https://httpbin.org/post foo=bar baz=quux < file.json -h "X-Foo: bar" -h "X-Baz: quux" -c "foo=bar; baz=quux" -c "foo=bar; baz=quux" -a "foo:bar" -t 10
```

### POST with form data and JSON, and multiple headers, and multiple cookies, and a basic auth, and a timeout, and a proxy

```bash
xh POST https://httpbin.org/post foo=bar baz=quux < file.json -h "X-Foo: bar" -h "X-Baz: quux" -c "foo=bar; baz=quux" -c "foo=bar; baz=quux" -a "foo:bar" -t 10 -x "http://localhost:8080"
```

### POST with form data and JSON, and multiple headers, and multiple cookies, and a basic auth, and a timeout, and a proxy, and a TLS certificate

```bash
xh POST https://httpbin.org/post foo=bar baz=quux < file.json -h "X-Foo: bar" -h "X-Baz: quux" -c "foo=bar; baz=quux" -c "foo=bar; baz=quux" -a "foo:bar" -t 10 -x "http://localhost:8080" -k "path/to/cert.pem"
```

## website

[https://github.com/ducaale/xh](https://github.com/ducaale/xh)

## help

```bash
xh 0.17.0
xh is a friendly and fast tool for sending HTTP requests

USAGE:
    xh [OPTIONS] <[METHOD] URL> [--] [REQUEST_ITEM]...

ARGS:
    <[METHOD] URL>       The request URL, preceded by an optional HTTP method
    <REQUEST_ITEM>...    Optional key-value pairs to be included in the request.

OPTIONS:
    -j, --json                           (default) Serialize data items from the command line as a JSON object
    -f, --form                           Serialize data items from the command line as form fields
    -m, --multipart                      Like --form, but force a multipart/form-data request even without files
        --raw <RAW>                      Pass raw request data without extra processing
        --pretty <STYLE>                 Controls output processing [possible values: all, colors, format, none]
    -s, --style <THEME>                  Output coloring style [possible values: auto, solarized, monokai, fruity]
        --response-charset <ENCODING>    Override the response encoding for terminal display purposes
        --response-mime <MIME_TYPE>      Override the response mime type for coloring and formatting for the terminal
    -p, --print <FORMAT>                 String specifying what the output should contain
    -h, --headers                        Print only the response headers. Shortcut for --print=h
    -b, --body                           Print only the response body. Shortcut for --print=b
    -v, --verbose                        Print the whole request as well as the response
        --all                            Show any intermediary requests/responses while following redirects with --follow
    -P, --history-print <FORMAT>         The same as --print but applies only to intermediary requests/responses
    -4, --ipv4                           Resolve hostname to ipv4 addresses only
    -6, --ipv6                           Resolve hostname to ipv6 addresses only
    -q, --quiet                          Do not print to stdout or stderr
    -S, --stream                         Always stream the response body
    -o, --output <FILE>                  Save output to FILE instead of stdout
    -d, --download                       Download the body to a file instead of printing it
    -c, --continue                       Resume an interrupted download. Requires --download and --output
        --session <FILE>                 Create, or reuse and update a session
        --session-read-only <FILE>       Create or read a session without updating it form the request/response exchange
    -A, --auth-type <AUTH_TYPE>          Specify the auth mechanism [possible values: basic, bearer, digest]
    -a, --auth <USER[:PASS] | TOKEN>     Authenticate as USER with PASS (-A basic|digest) or with TOKEN (-A bearer)
        --ignore-netrc                   Do not use credentials from .netrc
        --offline                        Construct HTTP requests without sending them anywhere
        --check-status                   (default) Exit with an error status code if the server replies with an error
    -F, --follow                         Do follow redirects
        --max-redirects <NUM>            Number of redirects to follow. Only respected if --follow is used
        --timeout <SEC>                  Connection timeout of the request
        --proxy <PROTOCOL:URL>           Use a proxy for a protocol. For example: --proxy https:http://proxy.host:8080
        --verify <VERIFY>                If "no", skip SSL verification. If a file path, use it as a CA bundle
        --cert <FILE>                    Use a client side certificate for SSL
        --cert-key <FILE>                A private key file to use with --cert
        --ssl <VERSION>                  Force a particular TLS version [possible values: auto, tls1, tls1.1, tls1.2, tls1.3]
        --https                          Make HTTPS requests if not specified in the URL
        --http-version <VERSION>         HTTP version to use [possible values: 1.0, 1.1, 2]
    -I, --ignore-stdin                   Do not attempt to read stdin
        --curl                           Print a translation to a curl command
        --curl-long                      Use the long versions of curl's flags
        --help                           Print help information
    -V, --version                        Print version information

Each option can be reset with a --no-OPTION argument.

Run `xh help` for more complete documentation.
xh 0.17.0
xh is a friendly and fast tool for sending HTTP requests.

It reimplements as much as possible of HTTPie's excellent design, with a focus on improved performance.

USAGE:
    xh [OPTIONS] <[METHOD] URL> [--] [REQUEST_ITEM]...

ARGS:
    <[METHOD] URL>
            The request URL, preceded by an optional HTTP method.
            
            If the method is omitted, it will default to GET, or to POST if the request contains a body.
            
            The URL scheme defaults to "http://" normally, or "https://" if the program is invoked as "xhs".
            
            A leading colon works as shorthand for localhost. ":8000" is equivalent to "localhost:8000", and ":/path" is equivalent to "localhost/path".

    <REQUEST_ITEM>...
            Optional key-value pairs to be included in the request.
            
            The separator is used to determine the type:
            
                key==value
                    Add a query string to the URL.
            
                key=value
                    Add a JSON property (--json) or form field (--form) to
                    the request body.
            
                key=@filename
                    Add a JSON property (--json) or form field (--form) from a
                    file to the request body.
            
                key:=value
                    Add a field with a literal JSON value to the request body.
            
                    Example: "numbers:=[1,2,3] enabled:=true"
            
                key:=@filename
                    Add a field with a literal JSON value from a file to the
                    request body.
            
                key@filename
                    Upload a file (requires --form or --multipart).
            
                    To set the filename and mimetype, ";type=" and
                    ";filename=" can be used respectively.
            
                    Example: "pfp@ra.jpg;type=image/jpeg;filename=profile.jpg"
            
                @filename
                    Use a file as the request body.
            
                header:value
                    Add a header, e.g. "user-agent:foobar"
            
                header:
                    Unset a header, e.g. "connection:"
            
                header;
                    Add a header with an empty value.
            
            A backslash can be used to escape special characters, e.g. "weird\:key=value".
            
            To construct a complex JSON object, the REQUEST_ITEM's key can be set to a JSON path instead of a field name.
            For more information on this syntax, refer to https://httpie.io/docs/cli/nested-json.

OPTIONS:
    -j, --json
            (default) Serialize data items from the command line as a JSON object.
            
            Overrides both --form and --multipart.

    -f, --form
            Serialize data items from the command line as form fields.
            
            Overrides both --json and --multipart.

    -m, --multipart
            Like --form, but force a multipart/form-data request even without files.
            
            Overrides both --json and --form.

        --raw <RAW>
            Pass raw request data without extra processing

        --pretty <STYLE>
            Controls output processing. Possible values are:
            
                all      (default) Enable both coloring and formatting
                colors   Apply syntax highlighting to output
                format   Pretty-print json and sort headers
                none     Disable both coloring and formatting
            
            Defaults to "format" if the NO_COLOR env is set and to "none" if stdout is not tty.

    -s, --style <THEME>
            Output coloring style
            
            [possible values: auto, solarized, monokai, fruity]

        --response-charset <ENCODING>
            Override the response encoding for terminal display purposes.
            
            Example: --response-charset=latin1

        --response-mime <MIME_TYPE>
            Override the response mime type for coloring and formatting for the terminal.
            
            Example: --response-mime=application/json

    -p, --print <FORMAT>
            String specifying what the output should contain.
            
            Use "H" and "B" for request header and body respectively, and "h" and "b" for response header and body.
            
            Example: --print=Hb

    -h, --headers
            Print only the response headers. Shortcut for --print=h

    -b, --body
            Print only the response body. Shortcut for --print=b

    -v, --verbose
            Print the whole request as well as the response.
            
            Additionally, this enables --all for printing intermediary requests/responses while following redirects.
            
            Equivalent to --print=HhBb --all.

        --all
            Show any intermediary requests/responses while following redirects with --follow

    -P, --history-print <FORMAT>
            The same as --print but applies only to intermediary requests/responses

    -4, --ipv4
            Resolve hostname to ipv4 addresses only

    -6, --ipv6
            Resolve hostname to ipv6 addresses only

    -q, --quiet
            Do not print to stdout or stderr

    -S, --stream
            Always stream the response body

    -o, --output <FILE>
            Save output to FILE instead of stdout

    -d, --download
            Download the body to a file instead of printing it.
            
            The Accept-Encoding header is set to identify and any redirects will be followed.

    -c, --continue
            Resume an interrupted download. Requires --download and --output

        --session <FILE>
            Create, or reuse and update a session.
            
            Within a session, custom headers, auth credentials, as well as any cookies sent by the server persist between requests.

        --session-read-only <FILE>
            Create or read a session without updating it form the request/response exchange

    -A, --auth-type <AUTH_TYPE>
            Specify the auth mechanism
            
            [possible values: basic, bearer, digest]

    -a, --auth <USER[:PASS] | TOKEN>
            Authenticate as USER with PASS (-A basic|digest) or with TOKEN (-A bearer).
            
            PASS will be prompted if missing. Use a trailing colon (i.e. "USER:") to authenticate with just a username.
            
            TOKEN is expected if --auth-type=bearer.

        --ignore-netrc
            Do not use credentials from .netrc

        --offline
            Construct HTTP requests without sending them anywhere

        --check-status
            (default) Exit with an error status code if the server replies with an error.
            
            The exit code will be 4 on 4xx (Client Error), 5 on 5xx (Server Error), or 3 on 3xx (Redirect) if --follow isn't set.
            
            If stdout is redirected then a warning is written to stderr.

    -F, --follow
            Do follow redirects

        --max-redirects <NUM>
            Number of redirects to follow. Only respected if --follow is used

        --timeout <SEC>
            Connection timeout of the request.
            
            The default value is "0", i.e., there is no timeout limit.

        --proxy <PROTOCOL:URL>
            Use a proxy for a protocol. For example: --proxy https:http://proxy.host:8080.
            
            PROTOCOL can be "http", "https" or "all".
            
            If your proxy requires credentials, put them in the URL, like so: --proxy http:socks5://user:password@proxy.host:8000.
            
            You can specify proxies for multiple protocols by repeating this option.
            
            The environment variables "http_proxy" and "https_proxy" can also be used, but are completely ignored if --proxy is passed.

        --verify <VERIFY>
            If "no", skip SSL verification. If a file path, use it as a CA bundle.
            
            Specifying a CA bundle will disable the system's built-in root certificates.
            
            "false" instead of "no" also works. The default is "yes" ("true").

        --cert <FILE>
            Use a client side certificate for SSL

        --cert-key <FILE>
            A private key file to use with --cert.
            
            Only necessary if the private key is not contained in the cert file.

        --ssl <VERSION>
            Force a particular TLS version.
            
            "auto" gives the default behavior of negotiating a version with the server.
            
            [possible values: auto, tls1, tls1.1, tls1.2, tls1.3]

        --https
            Make HTTPS requests if not specified in the URL

        --http-version <VERSION>
            HTTP version to use
            
            [possible values: 1.0, 1.1, 2]

    -I, --ignore-stdin
            Do not attempt to read stdin.
            
            This disables the default behaviour of reading the request body from stdin when a redirected input is detected.
            
            It is recommended to pass this flag when using xh for scripting purposes. For more information, refer to https://httpie.io/docs/cli/best-practices.

        --curl
            Print a translation to a curl command.
            
            For translating the other way, try https://curl2httpie.online/.

        --curl-long
            Use the long versions of curl's flags

        --help
            Print help information

    -V, --version
            Print version information

Each option can be reset with a --no-OPTION argument.
```