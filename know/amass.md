# amass

## Description

Amass is a tool used to enumerate subdomains of domains. It is a passive network mapper that discovers valid subdomains for any target domain by leveraging data sources such as the Certificate Transparency logs, DNS records, and reverse DNS records.

## install

```bash
brew tap caffix/amass
brew install amass
```

## sample usage

```bash
amass enum -d example.com
```

### sample output

```bash
example.com
www.example.com
mail.example.com
```

## help

```bash
amass --help

        .+++:.            :                             .+++.
      +W@@@@@@8        &+W@#               o8W8:      +W@@@@@@#.   oW@@@W#+
     &@#+   .o@##.    .@@@o@W.o@@o       :@@#&W8o    .@#:  .:oW+  .@#+++&#&
    +@&        &@&     #@8 +@W@&8@+     :@W.   +@8   +@:          .@8
    8@          @@     8@o  8@8  WW    .@W      W@+  .@W.          o@#:
    WW          &@o    &@:  o@+  o@+   #@.      8@o   +W@#+.        +W@8:
    #@          :@W    &@+  &@+   @8  :@o       o@o     oW@@W+        oW@8
    o@+          @@&   &@+  &@+   #@  &@.      .W@W       .+#@&         o@W.
     WW         +@W@8. &@+  :&    o@+ #@      :@W&@&         &@:  ..     :@o
     :@W:      o@# +Wo &@+        :W: +@W&o++o@W. &@&  8@#o+&@W.  #@:    o@+
      :W@@WWWW@@8       +              :&W@@@@&    &W  .o#@@W&.   :W@WWW@@&
        +o&&&&+.                                                    +oooo.

                                                                     v3.21.2
                                           OWASP Amass Project - @owaspamass
                         In-depth Attack Surface Mapping and Asset Discovery


Usage: amass intel|enum|viz|track|db [options]

  -h	Show the program usage message
  -help
    	Show the program usage message
  -version
    	Print the version number of this Amass binary


Subcommands: 

	amass intel - Discover targets for enumerations
	amass enum  - Perform enumerations and network mapping
	amass viz   - Visualize enumeration results
	amass track - Track differences between enumerations
	amass db    - Manipulate the Amass graph database

The user's guide can be found here: 
https://github.com/OWASP/Amass/blob/master/doc/user_guide.md

An example configuration file can be found here: 
https://github.com/OWASP/Amass/blob/master/examples/config.ini

The Amass tutorial can be found here: 
https://github.com/OWASP/Amass/blob/master/doc/tutorial.md
```
