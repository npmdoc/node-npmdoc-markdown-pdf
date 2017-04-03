# api documentation for  [markdown-pdf (v7.0.0)](https://github.com/alanshaw/markdown-pdf)  [![npm package](https://img.shields.io/npm/v/npmdoc-markdown-pdf.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-markdown-pdf) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-markdown-pdf.svg)](https://travis-ci.org/npmdoc/node-npmdoc-markdown-pdf)
#### Markdown to PDF converter

[![NPM](https://nodei.co/npm/markdown-pdf.png?downloads=true)](https://www.npmjs.com/package/markdown-pdf)

[![apidoc](https://npmdoc.github.io/node-npmdoc-markdown-pdf/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-markdown-pdf_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-markdown-pdf/build..beta..travis-ci.org/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-markdown-pdf/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-markdown-pdf/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Alan Shaw"
    },
    "bin": {
        "markdown-pdf": "bin/markdown-pdf"
    },
    "bugs": {
        "url": "https://github.com/alanshaw/markdown-pdf/issues"
    },
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
    "description": "Markdown to PDF converter",
    "devDependencies": {
        "coveralls": "^2.10.0",
        "istanbul": "^0.4.0",
        "pdf-text": "^0.4.0",
        "standard": "^5.4.1",
        "tape": "^4.2.2"
    },
    "directories": {},
    "dist": {
        "shasum": "3c70e09a6ef3dae2c5059b3a2294bd6581d269ce",
        "tarball": "https://registry.npmjs.org/markdown-pdf/-/markdown-pdf-7.0.0.tgz"
    },
    "engines": {
        "node": ">=0.10.0"
    },
    "gitHead": "62a12b3de8f70ac04e92eed11bb380ae7a37bdf2",
    "homepage": "https://github.com/alanshaw/markdown-pdf",
    "keywords": [
        "markdown",
        "pdf",
        "convert",
        "template"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "alanshaw",
            "email": "alan138@gmail.com"
        }
    ],
    "name": "markdown-pdf",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/alanshaw/markdown-pdf.git"
    },
    "scripts": {
        "coveralls": "cat ./coverage/lcov.info | coveralls",
        "test": "standard && istanbul cover node_modules/.bin/tape test/*.js"
    },
    "standard": {
        "ignore": [
            "html5bp/**"
        ]
    },
    "version": "7.0.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module markdown-pdf](#apidoc.module.markdown-pdf)



# <a name="apidoc.module.markdown-pdf"></a>[module markdown-pdf](#apidoc.module.markdown-pdf)



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
