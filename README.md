[![Build Status](https://travis-ci.com/gortc/turn.svg)](https://travis-ci.com/gortc/turn)
[![Build status](https://ci.appveyor.com/api/projects/status/bodd3l5hgu1agxpf/branch/master?svg=true)](https://ci.appveyor.com/project/ernado/turn-gvuk2/branch/master)
[![GoDoc](https://godoc.org/github.com/gortc/turn?status.svg)](http://godoc.org/github.com/gortc/turn)
[![Coverage Status](https://coveralls.io/repos/github/gortc/turn/badge.svg?branch=master&cache=1)](https://coveralls.io/github/gortc/turn?branch=master)
[![Go Report](https://goreportcard.com/badge/github.com/gortc/turn)](http://goreportcard.com/report/gortc/turn)


# TURN

Package turn implements TURN [[RFC 5766](https://tools.ietf.org/html/rfc5766)] Traversal Using Relays around NAT.
Complies to [gortc principles](https://github.com/gortc/dev/blob/master/README.md#principles) as core package.
Based on [gortc/stun](https://github.com/gortc/stun) package.
Work in progress.

## RFCs

The package aims to implement the follwing RFCs. Note that the requirement status is based on the [WebRTC spec](https://tools.ietf.org/html/draft-ietf-rtcweb-overview), focusing on data channels for now.

rfc | status | requirement | description
----|--------|-------------|----
[![RFC5766](https://img.shields.io/badge/RFC-5766-blue.svg)](https://tools.ietf.org/html/rfc5766) | ![status](https://img.shields.io/badge/status-beta-green.svg) | [![status](https://img.shields.io/badge/requirement-MUST-green.svg)](https://tools.ietf.org/html/rfc2119) | Traversal Using Relays around NAT
[![RFC6156](https://img.shields.io/badge/RFC-6156-blue.svg)](https://tools.ietf.org/html/rfc6156) | ![status](https://img.shields.io/badge/status-research-orange.svg) | [![status](https://img.shields.io/badge/requirement-MUST-green.svg)](https://tools.ietf.org/html/rfc2119) | TURN Extension for IPv6
[(TLS-over-)TCP](https://tools.ietf.org/html/rfc5766#section-2.1) | ![status](https://img.shields.io/badge/status-research-orange.svg) | [![status](https://img.shields.io/badge/requirement-MUST-green.svg)](https://tools.ietf.org/html/rfc2119) | Sending over TCP or TLS-over-TCP

## Benchmarks


```
goos: linux
goarch: amd64
pkg: github.com/gortc/turn
PASS
benchmark                                 iter     time/iter     throughput   bytes alloc        allocs
---------                                 ----     ---------     ----------   -----------        ------
BenchmarkIsChannelData-12           2000000000    1.64 ns/op   6694.29 MB/s        0 B/op   0 allocs/op
BenchmarkChannelData_Encode-12       200000000    9.11 ns/op   1317.35 MB/s        0 B/op   0 allocs/op
BenchmarkChannelData_Decode-12       500000000    3.92 ns/op   3061.45 MB/s        0 B/op   0 allocs/op
BenchmarkChannelNumber/AddTo-12      100000000   12.60 ns/op                       0 B/op   0 allocs/op
BenchmarkChannelNumber/GetFrom-12    200000000    7.23 ns/op                       0 B/op   0 allocs/op
BenchmarkData/AddTo-12               100000000   18.80 ns/op                       0 B/op   0 allocs/op
BenchmarkData/AddToRaw-12            100000000   16.80 ns/op                       0 B/op   0 allocs/op
BenchmarkLifetime/AddTo-12           100000000   13.70 ns/op                       0 B/op   0 allocs/op
BenchmarkLifetime/GetFrom-12         200000000    7.10 ns/op                       0 B/op   0 allocs/op
ok  	github.com/gortc/turn	19.110s
```