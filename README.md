# borc

[![](https://img.shields.io/badge/made%20by-Protocol%20Labs-blue.svg?style=flat-square)](http://ipn.io)
[![](https://img.shields.io/badge/project-IPFS-blue.svg?style=flat-square)](http://ipfs.io/)
[![](https://img.shields.io/badge/freenode-%23ipfs-blue.svg?style=flat-square)](http://webchat.freenode.net/?channels=%23ipfs)
[![Coverage Status](https://coveralls.io/repos/github/dignifiedquire/borc/badge.svg?branch=master)](https://coveralls.io/github/dignifiedquire/borc?branch=master)
[![Dependency Status](https://david-dm.org/dignifiedquire/borc.svg?style=flat-square)](https://david-dm.org/dignifiedquire/borc)
[![Travis CI](https://travis-ci.org/dignifiedquire/borc.svg?branch=master)](https://travis-ci.org/dignifiedquire/borc)
[![Circle CI](https://circleci.com/gh/dignifiedquire/borc.svg?style=svg)](https://circleci.com/gh/dignifiedquire/borc)


> Encode and parse data in the Concise Binary Object Representation (CBOR) data format ([RFC7049](http://tools.ietf.org/html/rfc7049)) **as fast as possible**.


## About

This library is a fork of the awesome [node-cbor]([![standard-readme compliant](https://img.shields.io/badge/standard--readme-OK-green.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)
). It borrows a lot of the interface, but drops all streaming and async processing in favor of a minimal syn api and being as fast as possible.


## Installation

```bash
$ npm install --save borc
```

## Benchmarks

TODO

## Example

```javascript
const cbor = require('borc')
const assert = require('assert')

const encoded = cbor.encode(true) // returns <Buffer f5>
const decoded = cbor.decodeFirst(encoded)
// decoded is the unpacked object
assert.ok(obj === true)

// Use integers as keys
var m = new Map()
m.set(1, 2)
encoded = cbor.encode(m) // <Buffer a1 01 02>
```

## API

See https://dignifiedquire.github.io/borc for details

The sync encoding and decoding are exported as a
[leveldb encoding](https://github.com/Level/levelup#custom_encodings), as
`cbor.leveldb`.

## Supported types

The following types are supported for encoding:

* boolean
* number (including -0, NaN, and ±Infinity)
* string
* Array, Set (encoded as Array)
* Object (including null), Map
* undefined
* Buffer
* Date,
* RegExp
* url.URL
* [bignumber](https://github.com/MikeMcl/bignumber.js)

Decoding supports the above types, including the following CBOR tag numbers:

| Tag | Generated Type |
|-----|----------------|
| 0   | Date           |
| 1   | Date           |
| 2   | bignumber      |
| 3   | bignumber      |
| 4   | bignumber      |
| 5   | bignumber      |
| 32  | url.URL        |
| 35  | RegExp         |


## License

MIT
