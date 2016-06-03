# str 

[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/piniondb/store/master/LICENSE)
[![GoDoc](https://godoc.org/github.com/piniondb/str?status.svg)](https://godoc.org/github.com/piniondb/str)
[![Build Status](https://travis-ci.org/piniondb/str.svg?branch=master)](https://travis-ci.org/piniondb/str)
[![Language](https://img.shields.io/badge/language-go-blue.svg)](https://golang.org/)

Package str provides some routines to convert an unsigned integer value to its
English textual representation and a generalized delimiting routine. These
facilitate database testing by supporting the generation of a large number of
records with two generally unrelated sort orders.

## Example

The following complete program exemplifies the `str.Delimit()` and
`str.Quantity()` functions.

    package main
    
    import (
    	"fmt"
    	"github.com/piniondb/str"
    )
    
    func main() {
    	var val uint
    	f := func() string {
    		return str.Delimit(fmt.Sprintf("%d", val), ",", 3)
    	}
    	for _, val = range []uint{0, 5, 15, 121, 4320, 70123,
    		999321, 4032500, 50100438, 100000054} {
    		fmt.Printf("[%14s : %s]\n", f(), str.Quantity(val))
    	}
    }

The output from this program is the following.

    [             0 : zero]
    [             5 : five]
    [            15 : fifteen]
    [           121 : one hundred twenty one]
    [         4,320 : four thousand three hundred twenty]
    [        70,123 : seventy thousand one hundred twenty three]
    [       999,321 : nine hundred ninety nine thousand three hundred twenty one]
    [     4,032,500 : four million thirty two thousand five hundred]
    [    50,100,438 : fifty million one hundred thousand four hundred thirty eight]
    [   100,000,054 : one hundred million fifty four]

## License

str is released under the MIT License.

