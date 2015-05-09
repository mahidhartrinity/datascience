# CSRF

[![NPM Version][npm-image]][npm-url]
[![NPM Downloads][downloads-image]][downloads-url]
[![Node.js Version][node-image]][node-url]
[![Build Status][travis-image]][travis-url]
[![Test Coverage][coveralls-image]][coveralls-url]

Logic behind CSRF token creation and verification.
Read [Understanding-CSRF](https://github.com/pillarjs/understanding-csrf) for more information on CSRF.
Use this module to create custom CSRF middleware and what not.

### Install

```bash
$ npm install csrf
```

## API

```js
var tokens = require('csrf')(options)

var secret = tokens.secretSync()
var token  = tokens.create(secret)
var valid  = tokens.verify(secret, token)
```

### Options

- `secretLength: 18` - the byte length of the secret key
- `saltLength: 8` - the string length of the salt

#### tokens.secret([cb])

Asynchronously create a new `secret` of length `secretLength`.
If `cb` is not defined, a promise is returned.
You don't have to use this.

```js
tokens.secret().then(function (secret) {

})

tokens.secret(function (err, secret) {

})
```

#### var secret = tokens.secretSync()

Synchronous version of `tokens.secret()`

#### var token = tokens.create(secret)

Create a CSRF token based on a `secret`.
This is the token you pass to clients.

#### var valid = tokens.verify(secret, token)

Check whether a CSRF token is valid based on a `secret`.
If it's not valid, you should probably throw a `403` error.

## License

[MIT](LICENSE)

[npm-image]: https://img.shields.io/npm/v/csrf.svg
[npm-url]: https://npmjs.org/package/csrf
[node-image]: https://img.shields.io/node/v/csrf.svg
[node-url]: http://nodejs.org/download/
[travis-image]: https://img.shields.io/travis/pillarjs/csrf/master.svg
[travis-url]: https://travis-ci.org/pillarjs/csrf
[coveralls-image]: https://img.shields.io/coveralls/pillarjs/csrf/master.svg
[coveralls-url]: https://coveralls.io/r/pillarjs/csrf?branch=master
[downloads-image]: https://img.shields.io/npm/dm/csrf.svg
[downloads-url]: https://npmjs.org/package/csrf
