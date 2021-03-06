# helper-copyright [![NPM version](https://img.shields.io/npm/v/helper-copyright.svg?style=flat)](https://www.npmjs.com/package/helper-copyright) [![NPM downloads](https://img.shields.io/npm/dm/helper-copyright.svg?style=flat)](https://npmjs.org/package/helper-copyright) [![Build Status](https://img.shields.io/travis/helpers/helper-copyright.svg?style=flat)](https://travis-ci.org/helpers/helper-copyright)

Template helper for adding a basic, one-line copyright statement, with formatting appropriate for LICENSE/LICENSE-MIT or README templates. Used with Verb, but should work with any Handlebars, Lo-Dash, underscore, or any template engine that allows helper functions to be registered.

## Install

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install helper-copyright --save
```

## Usage

```js
var copyright = require('helper-copyright');
var handlebars = require('handlebars');

// the top-level export is a function that must be called, so you 
// can optionally pass an options object when registering the helper
handlebars.registerHelper('copyright', copyright({linkify: true}));
```

## Example

Add a copyright statement, with author and year(s) in effect (verb templates):

```js
Copyright © 2016, [Jon Schlinkert](https://github.com/jonschlinkert).
//=> Copyright (c) 2016 Jon Schlinkert

Copyright © 2016, [Jon Schlinkert](https://github.com/jonschlinkert).
//=> Copyright (c) 2014-2016 Jon Schlinkert

Copyright © 2016, [Jon Schlinkert](https://github.com/jonschlinkert).
//=> Copyright (c) 2016 [Jon Schlinkert](https://github.com/jonschlinkert)
```

## Examples

> This should work with any engine, here are a few examples

Given the following locals:

```js
var locals = {author: {name: 'Jon Schlinkert', url: 'https://github.com/jonschlinkert'}};
```

### [Lo-Dash](https://github.com/jonschlinkert/template)

As a helper:

```js
_.template('<%= copyright({author: author}) %>', locals, {
  imports: {'helper-copyright': require('helper-copyright')}
});
//=> Copyright (c) 2016 Jon Schlinkert
```

As a mixin:

```js
_.mixin({'helper-copyright': require('helper-copyright')});
_.template('<%= copyright({author: author}) %>', locals);
//=> Copyright (c) 2016 Jon Schlinkert
```

### [template](https://github.com/jonschlinkert/template)

```js
template.helper('helper-copyright', require('helper-copyright'));
template.render('<%= copyright() %>', function(err, content) {
  console.log(content);
  //=> Copyright (c) 2016 Jon Schlinkert'
});
```

### [assemble](https://github.com/assemble/assemble)

```js
assemble.helper('helper-copyright', require('helper-copyright'));
assemble.render('{{copyright this}}', function(err, content) {
  console.log(content);
  //=> Copyright (c) 2016 Jon Schlinkert'
});
```

### [verb](https://github.com/jonschlinkert/verb)

```js
verb.helper('helper-copyright', require('helper-copyright'));
verb.render('Copyright © 2016, [Jon Schlinkert](https://github.com/jonschlinkert).', function(err, content) {
  console.log(content);
  //=> Copyright (c) 2016 Jon Schlinkert'
});
```

### [handlebars](https://github.com/wycats/handlebars.js/)

```js
var handlebars = require('handlebars');
handlebars.registerHelper('helper-copyright', require('helper-copyright'));
handlebars.compile('{{copyright this}}')(locals);
//=> Copyright (c) 2016 Jon Schlinkert
```

## Related projects

You might also be interested in these projects:

* [helper-license](https://www.npmjs.com/package/helper-license): Template helper for adding a formatted license statement based on the license type in package.json. | [homepage](https://github.com/helpers/helper-license)
* [helper-reflinks](https://www.npmjs.com/package/helper-reflinks): Async template helper for generating a list of markdown reference links. | [homepage](https://github.com/helpers/helper-reflinks)
* [helper-related](https://www.npmjs.com/package/helper-related): Template helper for generating a list of links to the homepages of related GitHub/npm projects. | [homepage](https://github.com/helpers/helper-related)
* [verb](https://www.npmjs.com/package/verb): Documentation generator for GitHub projects. Verb is extremely powerful, easy to use, and is used… [more](https://www.npmjs.com/package/verb) | [homepage](https://github.com/verbose/verb)

## Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/helpers/helper-copyright/issues/new).

## Building docs

Generate readme and API documentation with [verb](https://github.com/verbose/verb):

```sh
$ npm install verb && npm run docs
```

Or, if [verb](https://github.com/verbose/verb) is installed globally:

```sh
$ verb
```

## Running tests

Install dev dependencies:

```sh
$ npm install -d && npm test
```

## Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

## License

Copyright © 2016, [Jon Schlinkert](https://github.com/jonschlinkert).
Released under the [MIT license](https://github.com/helpers/helper-copyright/blob/master/LICENSE).

***

_This file was generated by [verb](https://github.com/verbose/verb), v0.9.0, on May 03, 2016._