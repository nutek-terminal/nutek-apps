# wafw00f

## Description
The Web Application Firewall Fingerprinting Tool. 
— From Enable Security

How does it work?

To do its magic, WAFW00F does the following:

Sends a normal HTTP request and analyses the response; this identifies a number of WAF solutions.
If that is not successful, it sends a number of (potentially malicious) HTTP requests and uses simple logic to deduce which WAF it is.
If that is also not successful, it analyses the responses previously returned and uses another simple algorithm to guess if a WAF or security solution is actively responding to our attacks.
For further details, check out the source code on our main repository.

## install

```
python setup.py install
```


## sample usage
```
wafw00f -a https://www.google.com
```

## sample output
```
   https://blackrock.com   Kona SiteDefender (Akamai)
   https://blackrock.com            Generic (Unknown)
```

## package info
```
Name         : wafw00f
Version      : 2.1.0
Release      : 10.fc37
Architecture : noarch
Size         : 331 k
Source       : wafw00f-2.1.0-10.fc37.src.rpm
Repository   : @System
From repo    : fedora
Summary      : Tool to identifies and fingerprints Web Application Firewall (WAF)
URL          : https://github.com/sandrogauci/wafw00f
License      : BSD
Description  : WAFW00F identifies and fingerprints Web Application Firewall (WAF) products.
```

## help
```
Usage: wafw00f url1 [url2 [url3 ... ]]
example: wafw00f http://www.victim.org/

Options:
  -h, --help            show this help message and exit
  -v, --verbose         Enable verbosity, multiple -v options increase
                        verbosity
  -a, --findall         Find all WAFs which match the signatures, do not stop
                        testing on the first one
  -r, --noredirect      Do not follow redirections given by 3xx responses
  -t TEST, --test=TEST  Test for one specific WAF
  -o OUTPUT, --output=OUTPUT
                        Write output to csv, json or text file depending on
                        file extension. For stdout, specify - as filename.
  -i INPUT, --input-file=INPUT
                        Read targets from a file. Input format can be csv,
                        json or text. For csv and json, a `url` column name or
                        element is required.
  -l, --list            List all WAFs that WAFW00F is able to detect
  -p PROXY, --proxy=PROXY
                        Use an HTTP proxy to perform requests, examples:
                        http://hostname:8080, socks5://hostname:1080,
                        http://user:pass@hostname:8080
  -V, --version         Print out the current version of WafW00f and exit.
  -H HEADERS, --headers=HEADERS
                        Pass custom headers via a text file to overwrite the
                        default header set.
```