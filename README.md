# npmdoc-markdown-pdf

#### api documentation for  [markdown-pdf (v7.0.0)](https://github.com/alanshaw/markdown-pdf)  [![npm package](https://img.shields.io/npm/v/npmdoc-markdown-pdf.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-markdown-pdf) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-markdown-pdf.svg)](https://travis-ci.org/npmdoc/node-npmdoc-markdown-pdf)

#### Markdown to PDF converter

[![NPM](https://nodei.co/npm/markdown-pdf.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/markdown-pdf)

- [https://npmdoc.github.io/node-npmdoc-markdown-pdf/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-markdown-pdf/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-markdown-pdf/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-markdown-pdf/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-markdown-pdf/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-markdown-pdf/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "name": "markdown-pdf",
    "version": "7.0.0",
    "description": "Markdown to PDF converter",
    "main": "index.js",
    "scripts": {
        "test": "standard && istanbul cover node_modules/.bin/tape test/*.js",
        "coveralls": "cat ./coverage/lcov.info | coveralls"
    },
    "repository": {
        "type": "git",
        "url": "git@github.com:alanshaw/markdown-pdf.git"
    },
    "keywords": [
        "markdown",
        "pdf",
        "convert",
        "template"
    ],
    "author": "Alan Shaw",
    "homepage": "https://github.com/alanshaw/markdown-pdf",
    "license": "MIT",
    "dependencies": {
        "commander": "^2.2.0",
        "duplexer": "^0.1.1",
        "extend": "^3.0.0",
        "highlight.js": "^9.1.0",
        "phantomjs-prebuilt": "^2.1.3",
        "remarkable": "^1.6.0",
        "stream-from-to": "^1.4.2",
        "through2": "^2.0.0",
        "tmp": "0.0.28"
    },
    "devDependencies": {
        "coveralls": "^2.10.0",
        "istanbul": "^0.4.0",
        "pdf-text": "^0.4.0",
        "standard": "^5.4.1",
        "tape": "^4.2.2"
    },
    "engines": {
        "node": ">=0.10.0"
    },
    "bin": {
        "markdown-pdf": "bin/markdown-pdf"
    },
    "standard": {
        "ignore": [
            "html5bp/**"
        ]
    }
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
