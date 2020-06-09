## CORS-Scanner

###  CORS misconfiguration scanner

CORS-Scanner is written in go, designed to discover CORS misconfigurations vulnerabilities of web application.

### Installation

If you have Go installed and configured (i.e. with $GOPATH/bin in your $PATH): you can install CORS-Scanner with `go get`:

```
▶ go get -u github.com/Tanmay-N/CORS-Scanner
```

### Usage 

```
CORS-Scanner -h 

  -o string
    	Set the Origin Header (Default=evil.collrabrator.com) (default "evil.collrabrator.com")
  -s string
    	Set the Cookie if required! (Default=Nill) (default "session=nulll")
```

CORS-Scanner accepts line-delimited domains on `stdin`:

``` 
▶ cat recon/example/domains.txt | httprobe > CORS-domain.txt
example.com
example.edu
example.net
```
```
▶ cat CORS-domain.txt | CORS-Scanner
[VULN - Found Misconfigured! Relefected Origin With Credentials True] Reflected Origin: evil.collrabrator.com, credentials: true, - URL: http://cors-test.example.com/test
[VULN - Found Misconfigured! Relefected Origin With Credentials True] Reflected Origin: evil.collrabrator.com, credentials: true, - URL: https://example.com/Account/Login?ReturnUrl=%2f
[VULN - Found Misconfigured! configured with Wildcard (*)] https://logcollector.api.example.jp
[VULN - Found Misconfigured! configured with Wildcard (*)] https://cloudcore.api.example.jp
[VULN - Found Misconfigured! configured with Wildcard (*)] https://photo.api.example.jp
```

Discover CORS misconfigurations for particular host:  

```
 ▶ echo "https://example.com/" | CORS-Scanner
 ```


