# mitmproxy

## Description

mitmproxy is an interactive TLS-capable intercepting HTTP proxy for penetration testers and software developers.

## Installation

```bash
brew install mitmproxy
```

## Usage

```bash
mitmproxy
```

## Resources

- [Features](https://docs.mitmproxy.org/stable/overview-features/)
- [User Guide](https://docs.mitmproxy.org/stable/)
- [GitHub](https://github.com/mitmproxy/mitmproxy)

## help

```bash
usage: mitmproxy [options]

options:
  -h, --help            show this help message and exit
  --version             show version number and exit
  --options             Show all options and their default values
  --commands            Show all commands and their signatures
  --set option[=value]  Set an option. When the value is omitted,
                        booleans are set to true, strings and
                        integers are set to None (if permitted),
                        and sequences are emptied. Boolean values
                        can be true, false or toggle. Sequences
                        are set using multiple invocations to set
                        for the same option.
  -q, --quiet           Quiet.
  -v, --verbose         Increase log verbosity.
  --mode MODE, -m MODE  The proxy server type(s) to spawn. Can be
                        passed multiple times. Mitmproxy supports
                        "regular" (HTTP), "transparent", "socks5",
                        "reverse:SPEC", and "upstream:SPEC" proxy
                        servers. For reverse and upstream proxy
                        modes, SPEC is host specification in the
                        form of "http[s]://host[:port]". You may
                        append `@listen_port` or
                        `@listen_host:listen_port` to override
                        `listen_host` or `listen_port` for a
                        specific proxy mode. Features such as
                        client playback will use the first mode to
                        determine which upstream server to use.
                        May be passed multiple times.
  --no-anticache
  --anticache           Strip out request headers that might cause
                        the server to return 304-not-modified.
  --no-showhost
  --showhost            Use the Host header to construct URLs for
                        display.
  --rfile PATH, -r PATH
                        Read flows from file.
  --scripts SCRIPT, -s SCRIPT
                        Execute a script. May be passed multiple
                        times.
  --stickycookie FILTER
                        Set sticky cookie filter. Matched against
                        requests.
  --stickyauth FILTER   Set sticky auth filter. Matched against
                        requests.
  --save-stream-file PATH, -w PATH
                        Stream flows to file as they arrive.
                        Prefix path with + to append. The full
                        path can use python strftime() formating,
                        missing directories are created as needed.
                        A new file is opened every time the
                        formatted string changes.
  --no-anticomp
  --anticomp            Try to convince servers to send us un-
                        compressed data.
  --console-layout {horizontal,single,vertical}
                        Console layout.
  --no-console-layout-headers
  --console-layout-headers
                        Show layout component headers

Proxy Options:
  --listen-host HOST    Address to bind proxy server(s) to (may be
                        overridden for individual modes, see
                        `mode`).
  --listen-port PORT, -p PORT
                        Port to bind proxy server(s) to (may be
                        overridden for individual modes, see
                        `mode`). By default, the port is mode-
                        specific. The default regular HTTP proxy
                        spawns on port 8080.
  --no-server, -n
  --server              Start a proxy server. Enabled by default.
  --ignore-hosts HOST   Ignore host and forward all traffic
                        without processing it. In transparent
                        mode, it is recommended to use an IP
                        address (range), not the hostname. In
                        regular mode, only SSL traffic is ignored
                        and the hostname should be used. The
                        supplied value is interpreted as a regular
                        expression and matched on the ip or the
                        hostname. May be passed multiple times.
  --allow-hosts HOST    Opposite of --ignore-hosts. May be passed
                        multiple times.
  --tcp-hosts HOST      Generic TCP SSL proxy mode for all hosts
                        that match the pattern. Similar to
                        --ignore-hosts, but SSL connections are
                        intercepted. The communication contents
                        are printed to the log in verbose mode.
                        May be passed multiple times.
  --upstream-auth USER:PASS
                        Add HTTP Basic authentication to upstream
                        proxy and reverse proxy requests. Format:
                        username:password.
  --proxyauth SPEC      Require proxy authentication. Format:
                        "username:pass", "any" to accept any
                        user/pass combination, "@path" to use an
                        Apache htpasswd file, or "ldap[s]:url_serv
                        er_ldap[:port]:dn_auth:password:dn_subtree
                        " for LDAP authentication.
  --no-rawtcp
  --rawtcp              Enable/disable raw TCP connections. TCP
                        connections are enabled by default.
  --no-http2
  --http2               Enable/disable HTTP/2 support. HTTP/2
                        support is enabled by default.

SSL:
  --certs SPEC          SSL certificates of the form
                        "[domain=]path". The domain may include a
                        wildcard, and is equal to "*" if not
                        specified. The file at path is a
                        certificate in PEM format. If a private
                        key is included in the PEM, it is used,
                        else the default key in the conf dir is
                        used. The PEM file should contain the full
                        certificate chain, with the leaf
                        certificate as the first entry. May be
                        passed multiple times.
  --cert-passphrase PASS
                        Passphrase for decrypting the private key
                        provided in the --cert option. Note that
                        passing cert_passphrase on the command
                        line makes your passphrase visible in your
                        system's process list. Specify it in
                        config.yaml to avoid this.
  --no-ssl-insecure
  --ssl-insecure, -k    Do not verify upstream server SSL/TLS
                        certificates.

Client Replay:
  --client-replay PATH, -C PATH
                        Replay client requests from a saved file.
                        May be passed multiple times.

Server Replay:
  --server-replay PATH, -S PATH
                        Replay server responses from a saved file.
                        May be passed multiple times.
  --no-server-replay-kill-extra
  --server-replay-kill-extra
                        Kill extra requests during replay (for
                        which no replayable response was found).
  --no-server-replay-nopop
  --server-replay-nopop
                        Don't remove flows from server replay
                        state after use. This makes it possible to
                        replay same response multiple times.
  --no-server-replay-refresh
  --server-replay-refresh
                        Refresh server replay responses by
                        adjusting date, expires and last-modified
                        headers, as well as adjusting cookie
                        expiration.

Map Remote:
  --map-remote PATTERN, -M PATTERN
                        Map remote resources to another remote URL
                        using a pattern of the form "[/flow-
                        filter]/url-regex/replacement", where the
                        separator can be any character. May be
                        passed multiple times.

Map Local:
  --map-local PATTERN   Map remote resources to a local file using
                        a pattern of the form "[/flow-filter]/url-
                        regex/file-or-directory-path", where the
                        separator can be any character. May be
                        passed multiple times.

Modify Body:
  --modify-body PATTERN, -B PATTERN
                        Replacement pattern of the form "[/flow-
                        filter]/regex/[@]replacement", where the
                        separator can be any character. The @
                        allows to provide a file path that is used
                        to read the replacement string. May be
                        passed multiple times.

Modify Headers:
  --modify-headers PATTERN, -H PATTERN
                        Header modify pattern of the form "[/flow-
                        filter]/header-name/[@]header-value",
                        where the separator can be any character.
                        The @ allows to provide a file path that
                        is used to read the header value string.
                        An empty header-value removes existing
                        header-name headers. May be passed
                        multiple times.

Filters:
  See help in mitmproxy for filter expression syntax.

  --intercept FILTER    Intercept filter expression.
  --view-filter FILTER  Limit the view to matching flows.
```