# api documentation for  [markdown-pdf (v7.0.0)](https://github.com/alanshaw/markdown-pdf)  [![npm package](https://img.shields.io/npm/v/npmdoc-markdown-pdf.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-markdown-pdf) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-markdown-pdf.svg)](https://travis-ci.org/npmdoc/node-npmdoc-markdown-pdf)
#### Markdown to PDF converter

[![NPM](https://nodei.co/npm/markdown-pdf.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/markdown-pdf)

[![apidoc](https://npmdoc.github.io/node-npmdoc-markdown-pdf/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-markdown-pdf/build/apidoc.html)

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
            "name": "alanshaw"
        }
    ],
    "name": "markdown-pdf",
    "optionalDependencies": {},
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
1.  [function <span class="apidocSignatureSpan"></span>markdown-pdf (opts)](#apidoc.element.markdown-pdf.markdown-pdf)
1.  [function <span class="apidocSignatureSpan">markdown-pdf.</span>toString ()](#apidoc.element.markdown-pdf.toString)



# <a name="apidoc.module.markdown-pdf"></a>[module markdown-pdf](#apidoc.module.markdown-pdf)

#### <a name="apidoc.element.markdown-pdf.markdown-pdf"></a>[function <span class="apidocSignatureSpan"></span>markdown-pdf (opts)](#apidoc.element.markdown-pdf.markdown-pdf)
- description and source-code
```javascript
function markdownpdf(opts) {
  opts = opts || {}
  opts.cwd = opts.cwd ? path.resolve(opts.cwd) : process.cwd()
  opts.phantomPath = opts.phantomPath || require('phantomjs-prebuilt').path
  opts.runningsPath = opts.runningsPath ? path.resolve(opts.runningsPath) : path.join(__dirname, 'runnings.js')
  opts.cssPath = opts.cssPath ? path.resolve(opts.cssPath) : path.join(__dirname, 'css', 'pdf.css')
  opts.highlightCssPath = opts.highlightCssPath ? path.resolve(opts.highlightCssPath) : path.join(__dirname, 'css', 'highlight.css
')
  opts.paperFormat = opts.paperFormat || 'A4'
  opts.paperOrientation = opts.paperOrientation || 'portrait'
  opts.paperBorder = opts.paperBorder || '2cm'
  opts.renderDelay = opts.renderDelay == null ? 0 : opts.renderDelay
  opts.loadTimeout = opts.loadTimeout == null ? 10000 : opts.loadTimeout
  opts.preProcessMd = opts.preProcessMd || function () { return through() }
  opts.preProcessHtml = opts.preProcessHtml || function () { return through() }
  opts.remarkable = extend({html: true, breaks: true}, opts.remarkable)
  opts.remarkable.preset = opts.remarkable.preset || 'default'
  opts.remarkable.plugins = opts.remarkable.plugins || []
  opts.remarkable.syntax = opts.remarkable.syntax || []

  var md = ''

  var mdToHtml = through(
    function transform (chunk, enc, cb) {
      md += chunk
      cb()
    },
    function flush (cb) {
      var self = this

      var mdParser = new Remarkable(opts.remarkable.preset, extend({
        highlight: function (str, lang) {
          if (lang && hljs.getLanguage(lang)) {
            try {
              return hljs.highlight(lang, str).value
            } catch (err) {}
          }

          try {
            return hljs.highlightAuto(str).value
          } catch (err) {}

          return ''
        }
      }, opts.remarkable))

      opts.remarkable.plugins.forEach(function (plugin) {
        if (plugin && typeof plugin === 'function') {
          mdParser.use(plugin)
        }
      })

      opts.remarkable.syntax.forEach(function (rule) {
        try {
          mdParser.core.ruler.enable([rule])
        } catch (err) {}
        try {
          mdParser.block.ruler.enable([rule])
        } catch (err) {}
        try {
          mdParser.inline.ruler.enable([rule])
        } catch (err) {}
      })

      self.push(mdParser.render(md))
      self.push(null)
    }
  )

  var inputStream = through()
  var outputStream = through()

  // Stop input stream emitting data events until we're ready to read them
  inputStream.pause()

  // Create tmp file to save HTML for phantom to process
  tmp.file({postfix: '.html'}, function (err, tmpHtmlPath, tmpHtmlFd) {
    if (err) return outputStream.emit('error', err)
    fs.close(tmpHtmlFd)

    // Create tmp file to save PDF to
    tmp.file({postfix: '.pdf'}, function (err, tmpPdfPath, tmpPdfFd) {
      if (err) return outputStream.emit('error', err)
      fs.close(tmpPdfFd)

      var htmlToTmpHtmlFile = fs.createWriteStream(tmpHtmlPath)

      htmlToTmpHtmlFile.on('finish', function () {
        // Invoke phantom to generate the PDF
        var childArgs = [
          path.join(__dirname, 'phantom', 'render.js'),
          tmpHtmlPath,
          tmpPdfPath,
          opts.cwd,
          opts.runningsPath,
          opts.cssPath,
          opts.highlightCssPath,
          opts.paperFormat,
          opts.paperOrientation,
          opts.paperBorder,
          opts.renderDelay,
          opts.loadTimeout
        ]

        childProcess.execFile(opts.phantomPath, childArgs, function (err, stdout, stderr) {
          // if (stdout) console.log(stdout)
          // if (stderr) console.error(stderr)
          if (err) return outputStream.emit('error', err)
          fs.createReadStream(tmpPdfPath).pipe(outputStream)
        })
      })

      // Setup the pipeline
      inputStream
        .pipe(opts.preProcessMd())
        .pipe(mdToHtml)
        .pipe(opts.preProcessHtml())
        .pipe(htmlToTmpHtmlFile)

      inputStream.resume()
    })
  })

  return extend(
    duplexer(inputStream, outputStream),
    streamft ...
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.markdown-pdf.toString"></a>[function <span class="apidocSignatureSpan">markdown-pdf.</span>toString ()](#apidoc.element.markdown-pdf.toString)
- description and source-code
```javascript
toString = function () {
    return toString;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
