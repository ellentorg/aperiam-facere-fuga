#@ellentorg/aperiam-facere-fuga <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

[![browser support][testling-svg]][testling-url]

An ES5 spec-compliant `Array.prototype.some` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://www.ecma-international.org/ecma-262/6.0/).

Because `Array.prototype.some` depends on a receiver (the “this” value), the main export takes the array to operate on as the first argument.

## Example

```js
var some = require('@ellentorg/aperiam-facere-fuga');
var assert = require('assert');

assert.equal(true, some([1, 2, 3], function (x) { return x === 2; }));
assert.equal(false, some([1, 2, 3], function (x) { return x === 4; }));
```

```js
var some = require('@ellentorg/aperiam-facere-fuga');
var assert = require('assert');
/* when Array#some is not present */
delete Array.prototype.some;
var shimmedSome = some.shim();
assert.equal(shimmedSome, some.getPolyfill());
var arr = [1, 2, 3];
var threeOrLarger = function (x) { return x >= 3; };
assert.deepEqual(arr.some(threeOrLarger), some(arr, threeOrLarger));
```

```js
var some = require('@ellentorg/aperiam-facere-fuga');
var assert = require('assert');
/* when Array#some is present */
var shimmedSome = some.shim();
assert.equal(shimmedSome, Array.prototype.some);
assert.deepEqual(arr.some(threeOrLarger), some(arr, threeOrLarger));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@ellentorg/aperiam-facere-fuga
[npm-version-svg]: https://versionbadg.es/ellentorg/aperiam-facere-fuga.svg
[deps-svg]: https://david-dm.org/ellentorg/aperiam-facere-fuga.svg
[deps-url]: https://david-dm.org/ellentorg/aperiam-facere-fuga
[dev-deps-svg]: https://david-dm.org/ellentorg/aperiam-facere-fuga/dev-status.svg
[dev-deps-url]: https://david-dm.org/ellentorg/aperiam-facere-fuga#info=devDependencies
[testling-svg]: https://ci.testling.com/ellentorg/aperiam-facere-fuga.png
[testling-url]: https://ci.testling.com/ellentorg/aperiam-facere-fuga
[npm-badge-png]: https://nodei.co/npm/@ellentorg/aperiam-facere-fuga.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@ellentorg/aperiam-facere-fuga.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@ellentorg/aperiam-facere-fuga.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@ellentorg/aperiam-facere-fuga
[codecov-image]: https://codecov.io/gh/ellentorg/aperiam-facere-fuga/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/ellentorg/aperiam-facere-fuga/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/ellentorg/aperiam-facere-fuga
[actions-url]: https://github.com/ellentorg/aperiam-facere-fuga/actions
