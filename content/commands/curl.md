+++
title= "curl"
date= 2018-07-19T21:44:15-05:00
description = ""
weight = 1070
+++

## Download to STDOUT
```
curl http://www.example.com
```

## Save response to file

Save to specified file name:
```
curl -o my_file http://www.example.com
```

Save to file name from URL
```
curl -O http://www.example.com/index.html
```

## Fetch multiple files
```
curl -O http://www.example.com/this.html -O http://www.example.com/that.html
```

## Continue/Resume download
After interruption of a download, resume using where '-' in '-C -' indicates resume at offset that was already downloaded. Otherwise an offset value can be provided.
```
curl -C - http://www.example.com
```

## Follow redirects
```
curl -L http://www.example.com
```

## Limit rate of transfer
In this example limit rate of transger to 1000B per second
```
curl --limit-rate 1000B -O http://www.example.com/bigfile.html
```

## Fetch if modified before/after time
Works for FTP and HTTP
Fetch if modified after 12/21/2017
```
curl -z 21-Dec-17 http://www.example.com
```

Fetch if modified before 12/21/2017
```
curl -z -21-Dec-17 http://www.example.com
```

## HTTP Auth
```
curl -u username:password http://www.example.com
```

## FTP Auth
```
curl -u username:password -O ftp://www.example.com/index.html
```

## Upload to FTP
Upload one file
```
curl -u user:pass -T file.txt ftp://www.exmaple.com
```

Upload multiple files
```
curl -u user:pass -T "{file1.txt,file2.txt}" ftp://www.exmaple.com
```

Upload from STDIN
```
curl -u user:pass -T - ftp://www.exmaple.com/file.txt
```

## Verbose/Trace
Print protocol details
```
curl -v http://www.example.com
```

Dump data transfer
```
curl --trace http://www.exmaple.com
```

## Send Mail
```
curl --mail-from you@here.com --mail-rcpt them@there.com smtp://example.com
```

## Send cookies
Send from file
```
curl -b cookie_file http://www.example.com
```

Send value where name=value is a valid cookie string
```
curl -b "name=value" http://www.example.com
```

Send multiple cookies
```
curl -b "name1=value1; name2=value2" http://www.example.com
```

Skip session cookies
```
curl -b cookie_file -j http://www.example.com
```

## Save Cookies
```
curl -c cookie_file http://www.example.com
```

## Request Header
```
curl --header "HEADER1" --header "HEADER" http://www.example.com
```

## HTTP Method
Default method is GET but can specify POST, PATCH, PUT, and DELETE.  Wonder what else is supported
Post
```
curl -X POST http://www.example.com
```

Post with parameters
```
curl -X POST http://www.example.com?p1=v1&p2=v2
```

Post with parameters in request body
```
curl -X POST -d "p1=v1&p2=v2" http://www.example.com
```

Post with JSON in request body
```
curl -X POST -d "{'name':'value'}" http://www.example.com
```

Post with file in request body
```
curl -X POST -d @file.json http://www.example.com
```

Post form parameters
```
curl -X POST -F foo=bar -F bar=baz http://www.example.com
```

Post form parameters with upload
```
curl -X POST -F foo=bar -F bar=@file.png http://www.example.com
```

## Cookie File Format
Tab delimited set of cookies, one per line with the following values:
* domain - domain that created and read the variable
* flag - TRUE/FALSE value indicating if machine with domain can read the variable, usually set by browser based on value set for domain
* path - The path within the domain variable is valid for
* secure - TRUE/FALSE value indicating if secure connection is required to access variable
* expiration - Unix time variable will expire, which is number of seconds since  Jan 1, 1970 00:00:00 GMT
* name - name of variable
* value - value of variable

## Reference
* [Chapter 3: cURL | Conquering the Command Line |  Softcover.io](http://conqueringthecommandline.com/book/curl)
* [GitHub - bagder/everything-curl: The book documenting the curl project, the curl tool, libcurl and everything related to this.](https://github.com/bagder/everything-curl)
