# wfuzz
Wfuzz provides a framework to automate web applications security assessments and could help you to secure your web applications by finding and exploiting web application vulnerabilities.

## install

```
pip install wfuzz
```

## package info

```
Name         : wfuzz
Version      : 3.1.0
Release      : 8.fc37
Architecture : noarch
Size         : 1.1 M
Source       : wfuzz-3.1.0-8.fc37.src.rpm
Repository   : @System
From repo    : fedora
Summary      : Web fuzzer
URL          : http://wfuzz.io
License      : GPLv2
Description  : Wfuzz has been created to facilitate the task in web applications assessments
             : and it is based on a simple concept: it replaces any reference to the FUZZ
             : keyword by the value of a given payload.
```

## How it works
Wfuzz it is based on a simple concept: it replaces any reference to the FUZZ keyword by the value of a given payload.

A payload in Wfuzz is a source of data.

This simple concept allows any input to be injected in any field of an HTTP request, allowing to perform complex web security attacks in different web application components such as: parameters, authentication, forms, directories/files, headers, etc.

Wfuzz is more than a web brute forcer:

Wfuzz’s web application vulnerability scanner is supported by plugins.
Wfuzz is a completely modular framework and makes it easy for even the newest of Python developers to contribute. Building plugins is simple and takes little more than a few minutes.
Wfuzz exposes a simple language interface to the previous HTTP requests/responses performed using Wfuzz or other tools, such as Burp. This allows you to perform manual and semi-automatic tests with full context and understanding of your actions, without relying on a web application scanner underlying implementation.

## sample usage

```
wfuzz -w common_dirs.txt --hc 404 -c https://nutek.neosb.net/FUZZ
```

## sample output

```
********************************************************
* Wfuzz 3.1.0 - The Web Fuzzer                         *
********************************************************

Target: https://nutek.neosb.net/FUZZ
Total requests: 4613

=====================================================================
ID           Response   Lines    Word       Chars       Payload                                                                                                                                     
=====================================================================

000000201:   200        0 L      178 W      2260 Ch     "404"                                                                                                                                       
000000785:   301        7 L      11 W       162 Ch      "categories"                                                                                                                                
000001113:   301        7 L      11 W       162 Ch      "css"                                                                                                                                       
000001997:   301        7 L      11 W       162 Ch      "img"                                                                                                                                       
000001990:   301        7 L      11 W       162 Ch      "images"                                                                                                                                    
000002016:   200        3 L      666 W      6181 Ch     "index"                                                                                                                                     
000002019:   200        3 L      666 W      6181 Ch     "index.html"                                                                                                                                
000003064:   301        7 L      11 W       162 Ch      "posts"                                                                                                                                     
000003691:   200        0 L      6 W        902 Ch      "sitemap"                                                                                                                                   
000003695:   200        0 L      6 W        902 Ch      "sitemap.xml"                                                                                                                               
000003960:   301        7 L      11 W       162 Ch      "tags"                                                                                                                                      

Total time: 47.77582
Processed Requests: 4613
Filtered Requests: 4602
Requests/sec.: 96.55511
```

## small example

```
wfpayload -z range --zD 0-10 --oF list0_to_10
wfuzz -w list0_to_10 --hc 404 -c -Z  http://testphp.vulnweb.com/artists.php?artist=FUZZ
```

## example output

```
********************************************************
* Wfuzz 3.1.0 - The Web Fuzzer                         *
********************************************************

Target: http://testphp.vulnweb.com/artists.php?artist=FUZZ
Total requests: 11

=====================================================================
ID           Response   Lines    Word       Chars       Payload                                                                                                                                     
=====================================================================

000000007:   200        123 L    547 W      6193 Ch     "3"                                                                                                                                         
000000011:   200        104 L    364 W      4735 Ch     "9"                                                                                                                                         
000000010:   200        104 L    364 W      4735 Ch     "6"                                                                                                                                         
000000005:   200        104 L    364 W      4735 Ch     "5"                                                                                                                                         
000000009:   200        104 L    364 W      4735 Ch     "4"                                                                                                                                         
000000006:   200        123 L    547 W      6193 Ch     "2"                                                                                                                                         
000000001:   200        104 L    364 W      4735 Ch     "0"                                                                                                                                         
000000008:   200        104 L    364 W      4735 Ch     "7"                                                                                                                                         
000000002:   200        104 L    364 W      4735 Ch     "8"                                                                                                                                         
000000003:   200        123 L    547 W      6251 Ch     "1"                                                                                                                                         
000000004:   200        104 L    364 W      4735 Ch     "10"                                                                                                                                        

Total time: 1.271788
Processed Requests: 11
Filtered Requests: 0
Requests/sec.: 8.649236
```

## help

```
********************************************************
* Wfuzz 3.1.0 - The Web Fuzzer                         *
*                                                      *
* Version up to 1.4c coded by:                         *
* Christian Martorella (cmartorella@edge-security.com) *
* Carlos del ojo (deepbit@gmail.com)                   *
*                                                      *
* Version 1.4d to 3.1.0 coded by:                      *
* Xavier Mendez (xmendez@edge-security.com)            *
********************************************************

Usage:	wfuzz [options] -z payload,params <url>

	FUZZ, ..., FUZnZ  wherever you put these keywords wfuzz will replace them with the values of the specified payload.
	FUZZ{baseline_value} FUZZ will be replaced by baseline_value. It will be the first request performed and could be used as a base for filtering.


Options:
	-h                        : This help
	--help                    : Advanced help
	--version                 : Wfuzz version details
	-e <type>                 : List of available encoders/payloads/iterators/printers/scripts
	
	-c                        : Output with colors
	-v                        : Verbose information.
	--interact                : (beta) If selected,all key presses are captured. This allows you to interact with the program.
	
	-p addr                   : Use Proxy in format ip:port:type. Repeat option for using various proxies.
	                            Where type could be SOCKS4,SOCKS5 or HTTP if omitted.
	
	-t N                      : Specify the number of concurrent connections (10 default)
	-s N                      : Specify time delay between requests (0 default)
	-R depth                  : Recursive path discovery being depth the maximum recursion level (0 default)
	-D depth                  : Maximum link depth level (4 default)
	-L, --follow              : Follow HTTP redirections
	
	-u url                    : Specify a URL for the request.
	-z payload                : Specify a payload for each FUZZ keyword used in the form of type,parameters,encoder.
	                            A list of encoders can be used, ie. md5-sha1. Encoders can be chained, ie. md5@sha1.
	                            Encoders category can be used. ie. url
	                            Use help as a payload to show payload plugin's details (you can filter using --slice)
	-w wordlist               : Specify a wordlist file (alias for -z file,wordlist).
	-V alltype                : All parameters bruteforcing (allvars and allpost). No need for FUZZ keyword.
	-X method                 : Specify an HTTP method for the request, ie. HEAD or FUZZ
	
	-b cookie                 : Specify a cookie for the requests
	-d postdata               : Use post data (ex: "id=FUZZ&catalogue=1")
	-H header                 : Use header (ex:"Cookie:id=1312321&user=FUZZ")
	--basic/ntlm/digest auth  : in format "user:pass" or "FUZZ:FUZZ" or "domain\FUZ2Z:FUZZ"
	
	--hc/hl/hw/hh N[,N]+      : Hide responses with the specified code/lines/words/chars (Use BBB for taking values from baseline)
	--sc/sl/sw/sh N[,N]+      : Show responses with the specified code/lines/words/chars (Use BBB for taking values from baseline)
	--ss/hs regex             : Show/Hide responses with the specified regex within the content
```

## advanced help

```
********************************************************
* Wfuzz 3.1.0 - The Web Fuzzer                         *
*                                                      *
* Version up to 1.4c coded by:                         *
* Christian Martorella (cmartorella@edge-security.com) *
* Carlos del ojo (deepbit@gmail.com)                   *
*                                                      *
* Version 1.4d to 3.1.0 coded by:                      *
* Xavier Mendez (xmendez@edge-security.com)            *
********************************************************

Usage:	wfuzz [options] -z payload,params <url>

	FUZZ, ..., FUZnZ  wherever you put these keywords wfuzz will replace them with the values of the specified payload.
	FUZZ{baseline_value} FUZZ will be replaced by baseline_value. It will be the first request performed and could be used as a base for filtering.


Options:
	-h/--help                 : This help
	--help                    : Advanced help
	--filter-help             : Filter language specification
	--version                 : Wfuzz version details
	-e <type>                 : List of available encoders/payloads/iterators/printers/scripts
	
	--recipe <filename>       : Reads options from a recipe. Repeat for various recipes.
	--dump-recipe <filename>  : Prints current options as a recipe
	--oF <filename>           : Saves fuzz results to a file. These can be consumed later using the wfuzz payload.
	
	-c                        : Output with colors
	-v                        : Verbose information.
	-f filename,printer       : Store results in the output file using the specified printer (raw printer if omitted).
	-o printer                : Show results using the specified printer.
	--interact                : (beta) If selected,all key presses are captured. This allows you to interact with the program.
	--dry-run                 : Print the results of applying the requests without actually making any HTTP request.
	--prev                    : Print the previous HTTP requests (only when using payloads generating fuzzresults)
	--efield <expr>           : Show the specified language expression together with the current payload. Repeat for various fields.
	--field <expr>            : Do not show the payload but only the specified language expression. Repeat for various fields.
	
	-p addr                   : Use Proxy in format ip:port:type. Repeat option for using various proxies.
	                            Where type could be SOCKS4,SOCKS5 or HTTP if omitted.
	
	-t N                      : Specify the number of concurrent connections (10 default)
	-s N                      : Specify time delay between requests (0 default)
	-R depth                  : Recursive path discovery being depth the maximum recursion level.
	-D depth                  : Maximum link depth level.
	-L,--follow               : Follow HTTP redirections
	--ip host:port            : Specify an IP to connect to instead of the URL's host in the format ip:port
	-Z                        : Scan mode (Connection errors will be ignored).
	--req-delay N             : Sets the maximum time in seconds the request is allowed to take (CURLOPT_TIMEOUT). Default 90.
	--conn-delay N            : Sets the maximum time in seconds the connection phase to the server to take (CURLOPT_CONNECTTIMEOUT). Default 90.
	
	-A, --AA, --AAA           : Alias for -v -c and --script=default,verbose,discover respectively
	--no-cache                : Disable plugins cache. Every request will be scanned.
	--script=                 : Equivalent to --script=default
	--script=<plugins>        : Runs script's scan. <plugins> is a comma separated list of plugin-files or plugin-categories
	--script-help=<plugins>   : Show help about scripts.
	--script-args n1=v1,...   : Provide arguments to scripts. ie. --script-args grep.regex="<A href=\"(.*?)\">"
	
	-u url                    : Specify a URL for the request.
	-m iterator               : Specify an iterator for combining payloads (product by default)
	-z payload                : Specify a payload for each FUZZ keyword used in the form of name[,parameter][,encoder].
	                            A list of encoders can be used, ie. md5-sha1. Encoders can be chained, ie. md5@sha1.
	                            Encoders category can be used. ie. url
	                            Use help as a payload to show payload plugin's details (you can filter using --slice)
	--zP <params>             : Arguments for the specified payload (it must be preceded by -z or -w).
	--zD <default>            : Default parameter for the specified payload (it must be preceded by -z or -w).
	--zE <encoder>            : Encoder for the specified payload (it must be preceded by -z or -w).
	--slice <filter>          : Filter payload's elements using the specified expression. It must be preceded by -z.
	-w wordlist               : Specify a wordlist file (alias for -z file,wordlist).
	-V alltype                : All parameters bruteforcing (allvars and allpost). No need for FUZZ keyword.
	-X method                 : Specify an HTTP method for the request, ie. HEAD or FUZZ
	
	-b cookie                 : Specify a cookie for the requests. Repeat option for various cookies.
	-d postdata               : Use post data (ex: "id=FUZZ&catalogue=1")
	-H header                 : Use header (ex:"Cookie:id=1312321&user=FUZZ"). Repeat option for various headers.
	--basic/ntlm/digest auth  : in format "user:pass" or "FUZZ:FUZZ" or "domain\FUZ2Z:FUZZ"
	
	--hc/hl/hw/hh N[,N]+      : Hide responses with the specified code/lines/words/chars (Use BBB for taking values from baseline)
	--sc/sl/sw/sh N[,N]+      : Show responses with the specified code/lines/words/chars (Use BBB for taking values from baseline)
	--ss/hs regex             : Show/hide responses with the specified regex within the content
	--filter <filter>         : Show/hide responses using the specified filter expression (Use BBB for taking values from baseline)
	--prefilter <filter>      : Filter items before fuzzing using the specified expression. Repeat for concatenating filters.
```