+++
Categories = ["Development", "GoLang"]
Description = "How to perform cross compile on Golang"
Tags = ["Development", "golang"]
date = "2016-01-06T22:09:11+07:00"
title = "Cross compile golang"

+++

Since version 1.5 it has been easier to generate Go binary for another System.

Just use go build (dont use go install) with GOOS, GOARCH, and GOARM (for ARM based system)

for example generate main.go binary for freebsd/amd64:
    
    GOOS=freebsd GOARCH=amd64 go build main.go

and for generate android binary:
    
    GOOS=android GOARCH=arm GOARM=7 go build .
    
for list of supported GOOS and GOARCH please visit [the official golang environment documentation](http://golang.org/doc/install/source#environment)

*this article is referenced from [@rakyll post about Go Cross Compilation](https://medium.com/@rakyll/go-1-5-cross-compilation-488092ba44ec)