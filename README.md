#### Fork of Backbone.NativeAjax that doesn't consider 404s errors

Backbone.NativeAjax
===================

A drop-in replacement for Backbone.Ajax that uses only native XMLHttpRequest
methods for sync. It has no dependency on jQuery.

You might consider using the [window.fetch pollyfill](https://github.com/github/fetch)
coupled with [a simple plugin for Backbone](https://gist.github.com/akre54/9891fc85ff46afd85814)
instead of this project if you need better Promise or header support.

To Use:
-------
Load Backbone.NativeAjax with your favorite module loader or add as a script
tag after you have loaded Backbone in the page.

If loading with AMD or CommonJS you should set `Backbone.ajax` yourself:

```js
// AMD
define(['backbone', 'nativeajax'], function(Backbone, ajax) {
  Backbone.ajax = ajax;
});

// CommonJS
var Backbone = require('backbone');
Backbone.ajax = require('backbone.nativeajax');
```

Features:
---------
* Accepts `success` and `error` callbacks
* Set headers with a `headers` object
* `beforeSend`

Requirements:
-------------
NativeAjax uses XMLHttpRequest which is supported in modern browsers.
See the [compatibility chart](http://caniuse.com/#search=XMLHttpRequest).

It also makes use of `Function.prototype.bind` which can be easily pollyfilled
in older environments.

Set a `Promise` object on the global or on `Backbone.ajax` to return a promise.

Notes:
------
* The ajax function accepts a `success` and `error` callbacks. To return
  a promise object, set a global `Promise` or `Backbone.ajax.Promise`.
* Unlike jQuery, we don't automatically set the `X-Requested-With` header, so
  things like Rails' `request.xhr?` will break. If you need it, you can pass it
  in yourself.

Uses code from [Exoskeleton](https://github.com/paulmillr/exoskeleton). See that
project for more information and other features.
