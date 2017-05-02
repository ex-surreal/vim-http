[![Build Status](https://travis-ci.org/nicwest/vim-http.svg?branch=master)](https://travis-ci.org/nicwest/vim-http)
[![Powered by vital.vim](https://img.shields.io/badge/powered%20by-vital.vim-80273f.svg)](https://github.com/vim-jp/vital.vim)
vim-http
========

simple wrapper over curl and http syntax highlighting.


Usage
------

Write a raw http request

```http
GET http://httpbin.org/get HTTP/1.1
Host: httpbin.org
Accept: application/json
```

`:Http` will execute the request and display the response in a new buffer.

`:Http!` will execute the request as above and follow any redirects.

`:HttpShowCurl` displays the curl request that the plugin executes under the 
hood

`:HttpShowRequest` displays the internal object representing the request

`:HttpClean` will add Host and Content-Length headers

`:HttpAuth` will prompt for authorization credentials


Configuration
-------------

`g:vim_http_clean_before_do` if set to `1` (default) will clean a request before
sending it to curl. Disable this by setting this global to `0`


Tests
-----

The integration test use [httpbin](https://httpbin.org/), and assumes it
running locally. I use a 
[docker container](https://github.com/citizen-stig/dockerhttpbin):

```
docker pull citizenstig/httpbin
docker run -d=true -p 8000:8000 citizenstig/httpbin
```

To run the tests pull the 
[themis test suite](https://github.com/thinca/vim-themis) 
(you don't have to install it but you can if you want). I normally just dump it
in the plugin directory.

```
git clone git@github.com:thinca/vim-themis.git
./vim-themis/bin/themis --reporter dot test
```