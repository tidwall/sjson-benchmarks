# `sjson-benchmarks`

Benchmarks of SJSON alongside [encoding/json](https://golang.org/pkg/encoding/json/), 
[ffjson](https://github.com/pquerna/ffjson), 
[EasyJSON](https://github.com/mailru/easyjson),
and [Gabs](https://github.com/Jeffail/gabs)

```
Benchmark_SJSON-8                  	 3000000	       805 ns/op	    1077 B/op	       3 allocs/op
Benchmark_SJSON_ReplaceInPlace-8   	 3000000	       449 ns/op	       0 B/op	       0 allocs/op
Benchmark_JSON_Map-8               	  300000	     21236 ns/op	    6392 B/op	     150 allocs/op
Benchmark_JSON_Struct-8            	  300000	     14691 ns/op	    1789 B/op	      24 allocs/op
Benchmark_Gabs-8                   	  300000	     21311 ns/op	    6752 B/op	     150 allocs/op
Benchmark_FFJSON-8                 	  300000	     17673 ns/op	    3589 B/op	      47 allocs/op
Benchmark_EasyJSON-8               	 1500000	      3119 ns/op	    1061 B/op	      13 allocs/op
```

JSON document used:

```json
{
  "widget": {
    "debug": "on",
    "window": {
      "title": "Sample Konfabulator Widget",
      "name": "main_window",
      "width": 500,
      "height": 500
    },
    "image": { 
      "src": "Images/Sun.png",
      "hOffset": 250,
      "vOffset": 250,
      "alignment": "center"
    },
    "text": {
      "data": "Click Here",
      "size": 36,
      "style": "bold",
      "vOffset": 100,
      "alignment": "center",
      "onMouseUp": "sun1.opacity = (sun1.opacity / 100) * 90;"
    }
  }
}    
```

*These benchmarks were run on a MacBook Pro 15" 2.8 GHz Intel Core i7 using Go 1.8.*

Last run: May 10, 2017

## Usage

If you desire to run this current benchmarks on your local computer,
you need to install ``go`` and ``dep``.

```sh
# install go
brew install go
mkdir -p ~/go/src
export GOPATH=~/go
# install dep
brew install dep
```

Then you can get the repo and run the benchmarks

```sh
# get the repo source files
go get -u github.com/tidwall/sjson-benchmarks
# go to the sources files
cd $GOPATH/src/github.com/tidwall/sjson-benchmarks
# make sure you have the same packages version
dep ensure
# finally run the tests
go test -v -bench=.
```
