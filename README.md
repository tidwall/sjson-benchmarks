# `sjson-benchmarks`

Benchmarks of SJSON alongside [encoding/json](https://golang.org/pkg/encoding/json/), 
[ffjson](https://github.com/pquerna/ffjson), 
[EasyJSON](https://github.com/mailru/easyjson),
and [Gabs](https://github.com/Jeffail/gabs)

```
Benchmark_SJSON-8                  	3000000	    415.2 ns/op	   1005 B/op	      2 allocs/op
Benchmark_SJSON_ReplaceInPlace-8   13991337	    256.9 ns/op	      0 B/op	      0 allocs/op
Benchmark_Encoding_JSON_Map-8      	 409584	     8196 ns/op	   5183 B/op	    124 allocs/op
Benchmark_Encoding_JSON_Struct-8   	 760608	     4806 ns/op	   1061 B/op	     25 allocs/op
Benchmark_Gabs-8                   	 441423	     8095 ns/op	   5557 B/op	    124 allocs/op
Benchmark_FFJSON-8                 	 458751	     7817 ns/op	   3486 B/op	     50 allocs/op
Benchmark_EasyJSON-8               	2360268	     1498 ns/op	   1061 B/op	     13 allocs/op
```

*These benchmarks were run on a MacBook Pro 14" 8C M1 Pro using Go 1.20.*

Last run: March 09, 2023

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
