# jid
Json Incremental Digger

It's a very simple tool.  
You can drill down JSON interactively by using filtering queries like [jq](https://stedolan.github.io/jq/).

**Suggestion** and **Auto completion** of this tool will provide you a very comfortable JSON drill down.

## Demo

![demo-jid-main](https://github.com/simeji/jid/wiki/images/demo-jid-main-640.gif)

## Installation

* [With homebrew taps (for Mac)](#with-homebrew-taps-for-mac)  
* [Simply use "jid" command](#simply-use-jid-command)  
* [Build](#build)  

### With homebrew taps (for Mac)

```
brew tap simeji/jid
brew install jid
```

### Simply use "jid" command

If you simply want to use `jid` command, please download binary from below.

https://github.com/simeji/jid/releases

## Build

Building jid requires some packages.

```
go get github.com/bitly/go-simplejson
go get github.com/nsf/termbox-go
go get github.com/pkg/errors
go get github.com/stretchr/testify/assert
```

## Usage

### Quick start

* [simple json example](#simple-json-example)  
* [simple json example2](#simple-json-example2)  
* [with initial query](#with-initial-query)  
* [with curl](#with-curl)  

#### simple json example

Please execute the below command.

```
echo '{"aa":"2AA2","bb":{"aaa":[123,"cccc",[1,2]],"c":321}}'| jid
```

then, jid will be running.

You can dig JSON data incrementally.

When you enter `.bb.aaa[2]`, you will see the following.

```
[Filter]> .bb.aaa[2]
[
  1,
  2
]
```

Then, you press Enter key and output `[1,2]` and exit.

#### simple json example2

This json is used by [demo section](https://github.com/simeji/jid#demo).
```
echo '{"info":{"date":"2016-10-23","version":1.0},"users":[{"name":"simeji","uri":"https://github.com/simeji","id":1},{"name":"simeji2","uri":"https://example.com/simeji","id":2},{"name":"simeji3","uri":"https://example.com/simeji3","id":3}],"userCount":3}}'|jid
```

#### With initial query

First argument of `jid` is initial query.
(Use JSON same as [Demo](#demo))

![demo-jid-with-query](https://github.com/simeji/jid/wiki/images/demo-jid-with-query-640.gif)

#### with curl

Sample for using [RDAP](https://datatracker.ietf.org/wg/weirds/documents/) data.

```
curl -s http://rdg.afilias.info/rdap/domain/example.info | jid
```

## Keymaps

|key|description|
|:-----------|:----------|
|`TAB` / `CTRL` + `I` |Show available items and choice them|
|`CTRL` + `W` |Delete from the cursor to the start of the word|
|`CTRL` + `F` / Right Arrow (:arrow_right:)|To the first character of the 'Filter'|
|`CTRL` + `B` / Left Arrow (:arrow_left:)|To the end of the 'Filter'|
|`CTRL` + `A`|To the first character of the 'Filter'|
|`CTRL` + `E`|To the end of the 'Filter'|
|`CTRL` + `J`|Scroll json buffer 1 line downwards|
|`CTRL` + `K`|Scroll json buffer 1 line upwards|
|`CTRL` + `L`|Change view mode whole json or keys (only object)|

### Option

First argument: Initial query

-q : Print query (for jq)
