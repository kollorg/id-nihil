# @kollorg/id-nihil <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES2017 spec-compliant `Object.values` shim. Invoke its "shim" method to shim `Object.values` if it is unavailable or noncompliant.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://tc39.github.io/ecma262/#sec-@kollorg/id-nihil).

Most common usage:
```js
var assert = require('assert');
var values = require('@kollorg/id-nihil');

var obj = { a: 1, b: 2, c: 3 };
var expected = [1, 2, 3];

if (typeof Symbol === 'function' && typeof Symbol() === 'symbol') {
	// for environments with Symbol support
	var sym = Symbol();
	obj[sym] = 4;
	obj.d = sym;
	expected.push(sym);
}

assert.deepEqual(values(obj), expected);

if (!Object.values) {
	values.shim();
}

assert.deepEqual(Object.values(obj), expected);
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.com/package/@kollorg/id-nihil
[npm-version-svg]: https://versionbadg.es/kollorg/id-nihil.svg
[deps-svg]: https://david-dm.org/kollorg/id-nihil.svg
[deps-url]: https://david-dm.org/kollorg/id-nihil
[dev-deps-svg]: https://david-dm.org/kollorg/id-nihil/dev-status.svg
[dev-deps-url]: https://david-dm.org/kollorg/id-nihil#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@kollorg/id-nihil.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@kollorg/id-nihil.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@kollorg/id-nihil.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@kollorg/id-nihil
[codecov-image]: https://codecov.io/gh/kollorg/id-nihil/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/kollorg/id-nihil/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/kollorg/id-nihil
[actions-url]: https://github.com/kollorg/id-nihil/actions
