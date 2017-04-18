# npmdoc-glob-stream

#### api documentation for  [glob-stream (v6.1.0)](https://github.com/gulpjs/glob-stream#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-glob-stream.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-glob-stream) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-glob-stream.svg)](https://travis-ci.org/npmdoc/node-npmdoc-glob-stream)

#### A Readable Stream interface over node-glob.

[![NPM](https://nodei.co/npm/glob-stream.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/glob-stream)

- [https://npmdoc.github.io/node-npmdoc-glob-stream/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-glob-stream/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-glob-stream/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-glob-stream/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-glob-stream/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-glob-stream/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Gulp Team",
        "url": "http://gulpjs.com/"
    },
    "bugs": {
        "url": "https://github.com/gulpjs/glob-stream/issues"
    },
    "contributors": [
        {
            "name": "Eric Schoffstall"
        },
        {
            "name": "Blaine Bublitz"
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
            "name": "contra"
        },
        {
            "name": "fractal"
        },
        {
            "name": "phated"
        }
    ],
    "name": "glob-stream",
    "optionalDependencies": {},
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



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
