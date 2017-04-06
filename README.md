# api documentation for  [glob-stream (v6.1.0)](https://github.com/gulpjs/glob-stream#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-glob-stream.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-glob-stream) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-glob-stream.svg)](https://travis-ci.org/npmdoc/node-npmdoc-glob-stream)
#### A Readable Stream interface over node-glob.

[![NPM](https://nodei.co/npm/glob-stream.png?downloads=true)](https://www.npmjs.com/package/glob-stream)

[![apidoc](https://npmdoc.github.io/node-npmdoc-glob-stream/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-glob-stream_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-glob-stream/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-glob-stream/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-glob-stream/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Gulp Team",
        "email": "team@gulpjs.com",
        "url": "http://gulpjs.com/"
    },
    "bugs": {
        "url": "https://github.com/gulpjs/glob-stream/issues"
    },
    "contributors": [
        {
            "name": "Eric Schoffstall",
            "email": "yo@contra.io"
        },
        {
            "name": "Blaine Bublitz",
            "email": "blaine.bublitz@gmail.com"
        }
    ],
    "dependencies": {
        "extend": "^3.0.0",
        "glob": "^7.1.1",
        "glob-parent": "^3.1.0",
        "is-negated-glob": "^1.0.0",
        "ordered-read-streams": "^1.0.0",
        "pumpify": "^1.3.5",
        "readable-stream": "^2.1.5",
        "remove-trailing-separator": "^1.0.1",
        "to-absolute-glob": "^2.0.0",
        "unique-stream": "^2.0.2"
    },
    "description": "A Readable Stream interface over node-glob.",
    "devDependencies": {
        "eslint": "^1.10.3",
        "eslint-config-gulp": "^2.0.0",
        "expect": "^1.19.0",
        "istanbul": "^0.4.3",
        "istanbul-coveralls": "^1.0.3",
        "jscs": "^2.4.0",
        "jscs-preset-gulp": "^1.0.0",
        "mississippi": "^1.2.0",
        "mocha": "^2.4.5"
    },
    "directories": {},
    "dist": {
        "shasum": "7045c99413b3eb94888d83ab46d0b404cc7bdde4",
        "tarball": "https://registry.npmjs.org/glob-stream/-/glob-stream-6.1.0.tgz"
    },
    "engines": {
        "node": ">= 0.10"
    },
    "files": [
        "index.js",
        "readable.js",
        "LICENSE"
    ],
    "gitHead": "8210a3c95cabc032088b1a0ff47ccbeb2f83ec52",
    "homepage": "https://github.com/gulpjs/glob-stream#readme",
    "keywords": [
        "glob",
        "stream",
        "gulp",
        "readable",
        "fs",
        "files"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "contra",
            "email": "contra@wearefractal.com"
        },
        {
            "name": "fractal",
            "email": "contact@wearefractal.com"
        },
        {
            "name": "phated",
            "email": "blaine.bublitz@gmail.com"
        }
    ],
    "name": "glob-stream",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/gulpjs/glob-stream.git"
    },
    "scripts": {
        "cover": "istanbul cover _mocha --report lcovonly",
        "coveralls": "npm run cover && istanbul-coveralls",
        "lint": "eslint . && jscs index.js readable.js test/",
        "pretest": "npm run lint",
        "test": "mocha --async-only"
    },
    "version": "6.1.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module glob-stream](#apidoc.module.glob-stream)
1.  [function <span class="apidocSignatureSpan">glob-stream.</span>readable (ourGlob, negatives, opt)](#apidoc.element.glob-stream.readable)
1.  object <span class="apidocSignatureSpan">glob-stream.</span>readable.prototype

#### [module glob-stream.readable](#apidoc.module.glob-stream.readable)
1.  [function <span class="apidocSignatureSpan">glob-stream.</span>readable (ourGlob, negatives, opt)](#apidoc.element.glob-stream.readable.readable)
1.  [function <span class="apidocSignatureSpan">glob-stream.readable.</span>super_ (options)](#apidoc.element.glob-stream.readable.super_)

#### [module glob-stream.readable.prototype](#apidoc.module.glob-stream.readable.prototype)
1.  [function <span class="apidocSignatureSpan">glob-stream.readable.prototype.</span>_read ()](#apidoc.element.glob-stream.readable.prototype._read)
1.  [function <span class="apidocSignatureSpan">glob-stream.readable.prototype.</span>destroy (err)](#apidoc.element.glob-stream.readable.prototype.destroy)



# <a name="apidoc.module.glob-stream"></a>[module glob-stream](#apidoc.module.glob-stream)

#### <a name="apidoc.element.glob-stream.readable"></a>[function <span class="apidocSignatureSpan">glob-stream.</span>readable (ourGlob, negatives, opt)](#apidoc.element.glob-stream.readable)
- description and source-code
```javascript
function GlobStream(ourGlob, negatives, opt) {
  if (!(this instanceof GlobStream)) {
    return new GlobStream(ourGlob, negatives, opt);
  }

  var ourOpt = extend({}, opt);

  Readable.call(this, {
    objectMode: true,
    highWaterMark: ourOpt.highWaterMark || 16,
  });

  // Delete 'highWaterMark' after inheriting from Readable
  delete ourOpt.highWaterMark;

  var self = this;

  function resolveNegatives(negative) {
    return toAbsoluteGlob(negative, ourOpt);
  }

  var ourNegatives = negatives.map(resolveNegatives);
  ourOpt.ignore = ourNegatives;

  var cwd = ourOpt.cwd;
  var allowEmpty = ourOpt.allowEmpty || false;

  // Extract base path from glob
  var basePath = ourOpt.base || getBasePath(ourGlob, ourOpt);

  // Remove path relativity to make globs make sense
  ourGlob = toAbsoluteGlob(ourGlob, ourOpt);
  // Delete 'root' after all resolving done
  delete ourOpt.root;

  var globber = new glob.Glob(ourGlob, ourOpt);
  this._globber = globber;

  var found = false;

  globber.on('match', function(filepath) {
    found = true;
    var obj = {
      cwd: cwd,
      base: basePath,
      path: removeTrailingSeparator(filepath),
    };
    if (!self.push(obj)) {
      globber.pause();
    }
  });

  globber.once('end', function() {
    if (allowEmpty !== true && !found && globIsSingular(globber)) {
      var err = new Error(globErrMessage1 + ourGlob + globErrMessage2);

      return self.destroy(err);
    }

    self.push(null);
  });

  function onError(err) {
    self.destroy(err);
  }

  globber.once('error', onError);
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.glob-stream.readable"></a>[module glob-stream.readable](#apidoc.module.glob-stream.readable)

#### <a name="apidoc.element.glob-stream.readable.readable"></a>[function <span class="apidocSignatureSpan">glob-stream.</span>readable (ourGlob, negatives, opt)](#apidoc.element.glob-stream.readable.readable)
- description and source-code
```javascript
function GlobStream(ourGlob, negatives, opt) {
  if (!(this instanceof GlobStream)) {
    return new GlobStream(ourGlob, negatives, opt);
  }

  var ourOpt = extend({}, opt);

  Readable.call(this, {
    objectMode: true,
    highWaterMark: ourOpt.highWaterMark || 16,
  });

  // Delete 'highWaterMark' after inheriting from Readable
  delete ourOpt.highWaterMark;

  var self = this;

  function resolveNegatives(negative) {
    return toAbsoluteGlob(negative, ourOpt);
  }

  var ourNegatives = negatives.map(resolveNegatives);
  ourOpt.ignore = ourNegatives;

  var cwd = ourOpt.cwd;
  var allowEmpty = ourOpt.allowEmpty || false;

  // Extract base path from glob
  var basePath = ourOpt.base || getBasePath(ourGlob, ourOpt);

  // Remove path relativity to make globs make sense
  ourGlob = toAbsoluteGlob(ourGlob, ourOpt);
  // Delete 'root' after all resolving done
  delete ourOpt.root;

  var globber = new glob.Glob(ourGlob, ourOpt);
  this._globber = globber;

  var found = false;

  globber.on('match', function(filepath) {
    found = true;
    var obj = {
      cwd: cwd,
      base: basePath,
      path: removeTrailingSeparator(filepath),
    };
    if (!self.push(obj)) {
      globber.pause();
    }
  });

  globber.once('end', function() {
    if (allowEmpty !== true && !found && globIsSingular(globber)) {
      var err = new Error(globErrMessage1 + ourGlob + globErrMessage2);

      return self.destroy(err);
    }

    self.push(null);
  });

  function onError(err) {
    self.destroy(err);
  }

  globber.once('error', onError);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.glob-stream.readable.super_"></a>[function <span class="apidocSignatureSpan">glob-stream.readable.</span>super_ (options)](#apidoc.element.glob-stream.readable.super_)
- description and source-code
```javascript
function Readable(options) {
  Duplex = Duplex || require('./_stream_duplex');

  if (!(this instanceof Readable)) return new Readable(options);

  this._readableState = new ReadableState(options, this);

  // legacy
  this.readable = true;

  if (options && typeof options.read === 'function') this._read = options.read;

  Stream.call(this);
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.glob-stream.readable.prototype"></a>[module glob-stream.readable.prototype](#apidoc.module.glob-stream.readable.prototype)

#### <a name="apidoc.element.glob-stream.readable.prototype._read"></a>[function <span class="apidocSignatureSpan">glob-stream.readable.prototype.</span>_read ()](#apidoc.element.glob-stream.readable.prototype._read)
- description and source-code
```javascript
_read = function () {
  this._globber.resume();
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.glob-stream.readable.prototype.destroy"></a>[function <span class="apidocSignatureSpan">glob-stream.readable.prototype.</span>destroy (err)](#apidoc.element.glob-stream.readable.prototype.destroy)
- description and source-code
```javascript
destroy = function (err) {
  var self = this;

  this._globber.abort();

  process.nextTick(function() {
    if (err) {
      self.emit('error', err);
    }
    self.emit('close');
  });
}
```
- example usage
```shell
...
  }
});

globber.once('end', function() {
  if (allowEmpty !== true && !found && globIsSingular(globber)) {
    var err = new Error(globErrMessage1 + ourGlob + globErrMessage2);

    return self.destroy(err);
  }

  self.push(null);
});

function onError(err) {
  self.destroy(err);
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
