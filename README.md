# koa-formidable

[![Build Status](https://api.travis-ci.org/lizouzt/koa-formidable.svg?branch=master)](https://travis-ci.org/lizouzt/koa-formidable)

[Formidable](https://github.com/felixge/node-formidable) middleware for Koa

**Breaking Change in 1.0.0:** both `body` and `files` are now added to Koa's `.request` instead of modifying the http request (`.req`) directly.

## API

`var formidable = require('koa-formidable')`

### formidable(opts)

Returns the formidable middleware that parses the incoming request and adds the `.request.body` and `.request.files` to the context.

**Arguments:**

* **opts** - the options that get passed to the [`Formidable.IncomingForm`](https://github.com/felixge/node-formidable#formidableincomingform) (you could also provide an instance of `IncomingForm` directly)

**Example:**

```js
var formidable = require('koa-formidable')
app.use(formidable())
```

### formidable.parse(opts, ctx)

Parse the incoming request manually.

**Arguments:**

* **opts** - the options that get passed to the [`Formidable.IncomingForm`](https://github.com/felixge/node-formidable#formidableincomingform) (you could also provide an instance of `IncomingForm` directly)
* **ctx** - the Koa context

**Example:**

```js
var formidable = require('koa-formidable')
app.use(function*(next) {
  var form = yield formidable.parse(this);
  
  var files     = form.files;
  var fields    = form.fields;
  ...
  yield next
})
```

## MIT License

Copyright (c) 2016
