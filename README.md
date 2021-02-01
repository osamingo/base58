# base58

[![CI](https://github.com/osamingo/base58/workflows/CI/badge.svg)](https://github.com/osamingo/base58/actions?query=workflow%3ACI)
[![codecov](https://codecov.io/gh/osamingo/Base58/branch/main/graph/badge.svg?token=gUDT8ydUMm)](https://codecov.io/gh/osamingo/Base58)
[![Go Report Card](https://goreportcard.com/badge/github.com/osamingo/base58)](https://goreportcard.com/report/github.com/osamingo/base58)
[![Go Reference](https://pkg.go.dev/badge/github.com/osamingo/base58.svg)](https://pkg.go.dev/github.com/osamingo/base58)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/osamingo/base58/blob/main/LICENSE)

## About

This `base58` package implements Logic optimized for unsigned int64.

## Install

```shell
$ go get -u github.com/osamingo/bae58
```

## Usage

```go
package main

import (
	"log"

	"github.com/osamingo/base58"
)

func main() {

	enc, err := base58.NewEncoder(base58.StandardSource)
	if err != nil {
		log.Fatal("failed to generate base58.Encoder", err)
	}

	src := uint64(9223372036854775808)
	dst := enc.Encode(src)

	log.Println(dst)
	// Output: NQm6nKp8qFD

	ret, err := enc.Decode(dst)
	if err != nil {
		log.Fatal("failed to decode, dst = "+dst, err)
	}

	log.Println(ret)
	// Output: 9223372036854775808
}
```

## Benchmark

```
# Machine: MacBook Pro (13-inch, 2018, Four Thunderbolt 3 Ports)
# CPU    : 2.7 GHz Intel Core i7
# Memory : 16 GB 2133 MHz LPDDR3

goos: darwin
goarch: amd64
pkg: github.com/osamingo/base58
BenchmarkEncoder_Encode-8   	15775299        71.5 ns/op      46 B/op      1 allocs/op
BenchmarkEncoder_Decode-8   	36928071        29.8 ns/op       0 B/op      0 allocs/op
PASS
```

## License

Released under the [MIT License](https://github.com/osamingo/base58/blob/main/LICENSE).
