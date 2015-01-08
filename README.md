parameter
=======

[![NPM version][npm-image]][npm-url]
[![build status][travis-image]][travis-url]
[![Test coverage][coveralls-image]][coveralls-url]
[![David deps][david-image]][david-url]
[![node version][node-image]][node-url]

[npm-image]: https://img.shields.io/npm/v/parameter.svg?style=flat-square
[npm-url]: https://npmjs.org/package/parameter
[travis-image]: https://img.shields.io/travis/node-modules/parameter.svg?style=flat-square
[travis-url]: https://travis-ci.org/node-modules/parameter
[coveralls-image]: https://img.shields.io/coveralls/node-modules/parameter.svg?style=flat-square
[coveralls-url]: https://coveralls.io/r/node-modules/parameter?branch=master
[david-image]: https://img.shields.io/david/node-modules/parameter.svg?style=flat-square
[david-url]: https://david-dm.org/node-modules/parameter
[node-image]: https://img.shields.io/badge/node.js-%3E=_0.10-green.svg?style=flat-square
[node-url]: http://nodejs.org/download/

![logo](https://raw.github.com/fengmk2/parameter/master/logo.png)

A parameter verify tools.

## Install

```bash
$ npm install parameter --save
```

## Usage

### API

- `validate(value, rule)` - validate the `value` conforms to `rule`. return an array of errors if break rule.

### Example

```js
var validate = require('parameter');

var data = {
  name: 'foo',
  age: 24,
  gender: 'male'
};

var rule = {
  name: 'string',
  age: 'int',
  gender: ['male', 'female', 'unknown']
};

var errors = validate(data, rule);
```

#### [complex example](example.js)

### Rule

#### common rule

- `required` - if `required` is set to false, this property can be empty. default to `true`.
- `type` - The type of property, every type has it's own rule for the validate.

#### int

If type is `int`, there has tow addition rules:

- `max` - The maximum of the value, `value` must <= `max`.
- `min` - The minimum of the value, `value` must >= `min`.

#### integer

Alias to `int`.

#### number

If type is `number`, there has tow addition rules:

- `max` - The maximum of the value, `value` must <= `max`.
- `min` - The minimum of the value, `value` must >= `min`.

#### date

The `date` type want to match `YYYY-MM-DD` type date string.

#### dateTime

The `dateTime` type want to match `YYYY-MM-DD HH:mm:ss` type date string.

#### id

The `id` type want to match `/^\d+$/` type date string.

#### boolean

Match `boolean` type value.

#### bool

Alias to `boolean`

#### string

If type is `string`, there has four addition rules:

- `allowEmpty`(alias to `empty`) - allow empty string, default to false.
- `format` - A `RegExp` to check string's format.
- `max` - The maximum length of the string.
- `min` - The minimum length of the string.

#### enum

If type is `enum`, it requires an addition rule:

- `values` - An array of data, `value` must be one on them. ___this rule is required.___

#### object

If type is `object`, there has one addition rule:

- `rule` - An object that validate the properties ot the object.

#### array

If type is `array`, there has tow addition rule:

- `itemType` - The type of every item in this array.
- `rule` - An object that validate the items of the array. Only work with `itemType`.

#### abbr

- `'int'` => `{type: 'int', required: true}`
- `'integer'` => `{type: 'integer', required: true}`
- `'number'` => `{type: 'number', required: true}`
- `'date'` => `{type: 'date', required: true}`
- `'dateTime'` => `{type: 'dateTime', required: true}`
- `'id'` => `{type: 'id', required: true}`
- `'boolean'` => `{type: 'boolean', required: true}`
- `'bool'` => `{type: 'bool', required: true}`
- `'string'` => `{type: 'string', required: true, allowEmpty: false}`
- `'object'` => `{type: 'object', required: true}`
- `'array'` => `{type: 'array', required: true}`
- `[1, 2]` => `{type: 'enum', values: [1, 2]}`
```

## License

(The MIT License)

Copyright (c) 2015 fengmk2 &lt;fengmk2@gmail.com&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
