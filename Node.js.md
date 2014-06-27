# Node.js Cheatsheet

This is a collection of best practices, cheats and tips for doing safe sex with node.js, enjoy!

## Maintainability 

Maintainability comes out of a uniform and homogeneous codebase. The fact that multiple developers are expected to read and understand existing code must always be the top and foremost priority when authoring code. After all, we write code for the purpose of reading it.

To achieve codebase uniformity and homogeneity a certain set of rules must be agreed upon and honored by all authors. This document is about these rules. When applied properly, the whole codebase should look like it was authored by a single person.

## <a name='TOC'>Table of Contents</a>

  1. [Document Blocks](#docblocks)
  1. [Module Dependencies](#modules)
  1. [Module Format](#format)
  1. [Optimizations](#optimizations)
  1. [git dependencies](#git)

## <a name='docblocks'>Document Blocks</a>

Every method, function, property should be documented with JSDoc Tags. The [Google's Closure Compiler Annotation][gdocs] is used. The main reason being the richness of expression for describing complex data structures and creating primitives.

```js
/**
 * Helper for default value of date types.
 *
 * @param  {number} plusTime
 * @return {number} The JS timestamp the future.
 */
orm.defaultDate = function(plusTime) {
  return Date.now() + plusTime;
};
```

**[[⬆]](#TOC)**

## <a name='modules'>Module Dependencies</a>

For the Node environment the following format of requiring modules is advised:

  1. Require all core modules
  1. Require all packages
  1. Require all local modules

Each separated by a new line and if possible order by lower to higher level in the stack.

```js
// core modules
var util = require('util');

// packages
var __ = require('lodash'); // use double underscore for lodash
var Promise = require('bluebird'); // lodash is lower in the stack than promises
var express = require('express');

// local modules
var userCtrl = require('./controllers/user.ctrl');
```

> **Important**: All module dependencies must be declared on the top of the file, no exceptions.

**[[⬆]](#TOC)**

## <a name='format'>Module Format</a>

### General Layout

These rules only apply to Node modules. Each module should have the following structure:

Lines must not exceed 80 columns in any file. Exceptions are markdown and markup files.

1. The `@fileOverview` tag with a general description about what this module is about.
1. The module dependencies as described in [Module Dependencies](#modules).
1. Declare anything that is local to the module.
1. Use only `module.exports` as a way of exporting, before any code. Beyond this point everything is attached to the exported object.
1. Declare all static properties, functions, constants or enums right after the export statement.
1. Declare all public / exported methods
1. Declare all private methods

Even *private* methods are defined on the exported object.

```js
/**
 * @fileOverview The user Model.
 */
var util = require('util');

var __ = require('lodash');
var config = require('config');
var log = require('logg').getLogger('app.model.User');

var ModelMongo = require('./model-mongo');
var helpers = require('../util/helpers');

/**
 * The base user model.
 *
 * @constructor
 * @extends {app.ModelMongo}
 */
var User = module.exports = function(){
  ModelMongo.apply(this, arguments);
};
util.inherits(User, ModelMongo);
helpers.addSingletonGetter(User);

/**
 * The supported user roles.
 *
 * @enum {number}
 */
User.Role = {
  API: 1,
  ADMIN: 2,
};

/**
 * Pre-validation middleware. Set any default values.
 *
 * @param  {Function(Error)} next callback
 * @private
 * @this {mongoose.Schema} Mongoose context.
 */
User.prototype._setDefaultValues = function(next){
  next();
};

/**
 * Pre-Save password filter, will one-way encrypt the value.
 *
 * @param  {Function(Error=)} next Callback.
 * @this {mongoose.Schema} Mongoose context.
 * @private
 */
User.prototype._hashPassword = function(next) {
  next();
};
```
**[[⬆]](#TOC)**

## <a name='optimizations'>Optimizations</a>

Random snippets of best practices and performance gains.

#### Do not use .bind()

[Bind's implementation is slow][bind slow], until V8 gets passed that issue use closures:

```js

app.add = function(a, b) {

  // bad
  asyncFn(function() {
    this.a = a;
  }.bind(this));

  // good
  var self = this;
  asyncFn(function() {
    self.a = a;
  });  

};
```

#### Use .bind()

You can use `.bind()` during application boot-time for binding methods. Boot-time occurs only once so the performance hit by de-optimized methods and practices is non consequential.

[gdocs]: https://developers.google.com/closure/compiler/docs/js-for-compiler?hl=en#tags
[bind slow]: http://stackoverflow.com/questions/17638305/why-is-bind-slower-than-a-closure/17638540#17638540


**[[⬆]](#TOC)**

## <a name='git'>Git Dependencies</a>

### Require a public repository

```
npm install https://github.com/username/repository/tarball/branch-name --save
```

**[[⬆]](#TOC)**
