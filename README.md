# goperf - Performance tester
A highly concurrant web stack load tester.

### Running on a 32 CPU machine
![Alt text](readme_imgs/GoPerf.png?raw=true "GoPerf")

### Example Output
![Alt text](readme_imgs/GoPerfOutput.png?raw=true "Output")

## Setup
#### Ensure gopath is correctly setup

Make sure you have your GOPATH setup to point to the go/bin directory.
If you have a default go install on ubuntu it would be ~/go/bin.
If so you would add this to your path.
```
export PATH=$PATH:~/go/bin
```
#### Install

```
go get github.com/gnulnx/goperf
```

#### Build
```
go install github.com/gnulnx/goperf
```

## Usage:

### Fetch

Fetch a page and its assets and display info.  
```
./goperf -url {url} -fetch
```
This will print the an output like

![Alt text](readme_imgs/Fetch.png?raw=true "Fetch")

To Fetch a page and display all it's assets use:
```
./goperf -url {url} -fetch --printjson
```
NOTE this will print the content of the body in each of the fetched assets. If you have large minified JS bundles it will be pretty messy.


Fetch a page and it's assets (js, css, img) and return the bodies for the assets.
--printjson also pretty prints the json that is returned (above other output).
```
./goperf -url {url} -fetchall --printjson
```

Fetch a page that requires a session id (such as a django login)

```
./goperf -url http://192.168.33.11/student/ -fetchall -cookies "sessionid_vagrant=0xkfeev882n0i9efkiq7vmd2i6efufz9;" --printjson
```

### Basic perf test.

Fire a 3 second test with 3 simultaneous connections
```
./goperf -url {url} -sec=3 -connections=3
```



### Run minimal unit and benchmark tests
```
go test ./... -cover -bench
```
