# crypto-fs
Wrapper around node fs module that encrypts the files on the fly

[![Code Climate](https://codeclimate.com/github/DarkoKukovec/crypto-fs/badges/gpa.svg)](https://codeclimate.com/github/DarkoKukovec/crypto-fs)
[![Test Coverage](https://codeclimate.com/github/DarkoKukovec/crypto-fs/badges/coverage.svg)](https://codeclimate.com/github/DarkoKukovec/crypto-fs/coverage)
[![Build Status](https://travis-ci.org/DarkoKukovec/crypto-fs.svg?branch=master)](https://travis-ci.org/DarkoKukovec/crypto-fs)
[![Dependency Status](https://david-dm.org/DarkoKukovec/crypto-fs.svg)](https://david-dm.org/DarkoKukovec/crypto-fs)

## Installation

``npm install DarkoKukovec/crypto-fs``

## Initialization

    var fs = require('crypto-fs');
    fs.init({
      baseFs: require('fs'),
      algorithm: 'aes-256-ctr',
      prefix: '',
      password: '1234',
      root: './test/dest',
      iv: null,
      realSize: false
    });

### Options

* baseFs (default: ``require("fs")``)
  * What fs module should be used
* algorithm (default: ``"aes-256-ctr"``)
  * Any algorithm supported by node.js crypto module.
* prefix (default: ``""``)
  * Encrypted filename prefix.
* password (no default)
  * Please don't use 1234 as your password :)
* root (no default)
  * Root directory of the encrypted files.
* iv (default: ``null``)
  * If initialization vector is given, Cipheriv will be used.
* realSize (default: ``false``)
  * Encrypted files have marginaly bigger file size than the normal sizes. To get the real file size, the file needs to be decrypted, so set this to true only if you need to.

## Base FS

By default, this module relies on the native fs module, but this can be changed. If you have a different module that exposes the same methods (e.g. ftp-fs, s3-fs), you can set it as the base fs.
For every exposed method, it will be documented which methods does it require from the base fs. If you're using the default fs module, you can ignore this info.

## Implemented methods

* ``init`` (non-standard)
  * used to initialize the module (documented above)
  * required baseFs methods: ``existsSync``
