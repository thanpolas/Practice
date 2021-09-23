# Node.js Cheatsheet

This is a collection of best practices, cheats and tips for doing safe sex with node.js, enjoy!

## Maintainability 

Maintainability comes out of a uniform and homogeneous codebase. The fact that multiple developers are expected to read and understand existing code must always be the top and foremost priority when authoring code. After all, we write code for the purpose of reading it.

To achieve codebase uniformity and homogeneity a certain set of rules must be agreed upon and honored by all authors. This document is about these rules. When applied properly, the whole codebase should look like it was authored by a single person.

## <a name='TOC'>Table of Contents</a>

  1. [Formatting](#formatting)
  1. [Document Blocks](#docblocks)
  1. [Module Dependencies](#modules)
  1. [Module Format](#format)

## <a name='formatting'>Formatting</a>

Thanks to recent developments in tooling, we no longer have to argue about formatting on node.js (or any javascript) project. The only thing you have to do is have the [prettier](https://prettier.io/) package installed on your editor.

As, at this time (2021) the most popular editor is Visual Studio Code, to enable auto-formatting on save, you have to create the file `.vscode/settings.json` with the contents:

```json
{
    "editor.formatOnSave": true,
}
```

**[[⬆]](#TOC)**

## <a name='docblocks'>Document Blocks</a>

Every method, function, property should be documented with [JSDoc Tags][jsdoc].

```js
/**
 * Helper for default value of date types.
 *
 * @param  {number} plusTime The time to add in miliseconds.
 * @return {number} The JS timestamp the future.
 */
orm.defaultDate = function(plusTime) {
  return Date.now() + plusTime;
};
```

**[[⬆]](#TOC)**

## <a name='modules'>Module Dependencies</a>

For the Node environment the following order of requiring modules is advised:

1. Require all core modules
1. Require all packages
1. Require all local modules

Each separated by a new line and if possible order by lower to higher level in the stack.

```js
// core modules
const util = require('util');

// packages
const __ = require('lodash'); // use double underscore for lodash
const Promise = require('bluebird'); // lodash is lower in the stack than promises
const express = require('express');

// local modules
const userCtrl = require('./controllers/user.ctrl');
```

> **Important**: All module dependencies must be declared on the top of the file, no exceptions.

**[[⬆]](#TOC)**

## <a name='format'>Module Format</a>

### General Layout

Each Node.js module should have the following structure:

1. Lines must not exceed 80 columns. Exceptions are markdown and markup files.
1. The `@fileoverview` tag at the top of the module, with a general description about what this module is about.
1. The module dependencies as described in [Module Dependencies](#modules).
1. Use only `module.exports` as a way of exporting, before any code. Beyond this point everything is attached to the exported object.
1. Declare all static properties, functions, constants or enums right after the export statement.
1. Declare all public / exported methods
1. Declare all private methods

Even *private* methods are defined on the exported object.

```js
/**
 * @fileOverview The user Model.
 */

const util = require('util');

const __ = require('lodash');
const config = require('config');
const log = require('logg').getLogger('app.model.User');

const ModelMongo = require('./model-mongo');
const helpers = require('../util/helpers');

const user = (module.exports = {});

/**
 * The supported user roles.
 *
 * @enum {number}
 */
user.Role = {
  API: 1,
  ADMIN: 2,
};

/**
 * Pre-validation middleware. Set any default values.
 *
 * @param  {function<Error>} next callback
 * @private
 */
user._setDefaultValues = (next) => {
  next();
};
```
**[[⬆]](#TOC)**

[jsdoc]: https://jsdoc.app/
