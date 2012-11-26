# Underscore.Deferred

[![Build Status](https://secure.travis-ci.org/wookiehangover/underscore.deferred.png?branch=master)](http://travis-ci.org/wookiehangover/underscore.deferred)

v0.3.1 (jQuery 1.8.3)

This is a port of jQuery.Deferred as an Underscore mixin, but it can be
used without any depencencies. It currently matches the Deferred specifications
and implementation from jQuery 1.8.0, with all the associated helpers.

## Deferreds are great, let's take them everywhere

jQuery offers a robust, consistent and well documented API; this project aims
to make it portable. jQuery added a handful of helper methods to their
implementation of the [Common.js Promises/A Spec][promise] and they're faithfully
reproduced without any dependencies.

## Usage

underscore.deferred works on the server and in the browser.

In the browser, just require it like you would any other file. If you're
including Underscore on the page, make sure you include it before
underscore.deferred. If you don't have Underscore, the plugin attaches to
`window._`.

On the server, simply install via npm and include it with require:

    var _ = require('underscore.deferred');
    var dfd = new _.Deferred(); // tada!

Or if you'd like to use it as an Underscore or Lodash mixin:

    var _ = require('underscore');
    _.mixin( require('underscore.deferred') );

Underscore isn't a strict requirement, and assigning it to another
name will always work.

Addionally, underscore.Deferred can be used with [Ender.js][ender], if
you're still into that sort of thing.

## Enhancements / Changes

So far, there's only 1 substantial difference between the jQuery API and
underscore.deffered's. This may change in the future as new or
divergent functionality is tested out, but rest assured that all differences
will be called out here (and will have proper test coverage.)

###_.when

underscore.deferred will `apply` an Array if it's the only argument, providing a
useful shortcut for using `when` with an array of promises. Example:

    var form = _.Deferred();
    var auth = _.Deferred();

    var promises = [ form.promise(), auth.promise() ];

    _.when(promises).done(function(){
      // ...
    });

    form.resolve();
    auth.resolve();

## API

underscore.deferred is an implementation of the [jQuery.Deferred
API][jquery-docs]. Here are some of the methods implemented:

* [always](http://api.jquery.com/deferred.always/)
* [done](http://api.jquery.com/deferred.done/)
* [fail](http://api.jquery.com/deferred.fail/)
* [notify](http://api.jquery.com/deferred.notify/)
* [notifyWith](http://api.jquery.com/deferred.notifywith/)
* [pipe](http://api.jquery.com/deferred.pipe/)
* [promise](http://api.jquery.com/deferred.promise/)
* [reject](http://api.jquery.com/deferred.reject/)
* [rejectWith](http://api.jquery.com/deferred.rejectWith/)
* [resolve](http://api.jquery.com/deferred.resolve/)
* [resolveWith](http://api.jquery.com/deferred.resolve/)
* [state](http://api.jquery.com/deferred.notifywith/)
* [then](http://api.jquery.com/deferred.then/)
* [when](http://api.jquery.com/jQuery.when/)

For the complete API documentation, see [jQuery's Documentation][jquery-docs].

This project wouldn't exist if not for the the hard work and effort put
into jQuery by its core team and contributors--thanks for making this
possible!

## Minified Build

One time setup command:

```
$ npm install
```

To build with [grunt](https://github.com/cowboy/grunt)

```
$ grunt
```

To run headless Qunit tests (must have phantomjs in your path)

```
$ grunt qunit
```

## Contributors

* [rwldrn](https://github.com/rwldrn)
* [tbranyen](https://github.com/tbranyen)
* [taxillian](https://github.com/taxilian)
* [danheberden](https://github.com/danheberden)

## Roadmap

The goal is to slim the code footprint for robust deferreds as much as
possible while maintaining mixin integration with Underscore and faithfullness
to the jQuery API.

This is a work in progress, feel free to contribute.

## Release Notes

0.3.1 - updating to match jQuery 1.8.3

0.3.0 - adding divergent behavior for [_.when](https://github.com/wookiehangover/underscore.deferred#_when)

0.2.0 - updating to match jQuery 1.8.0

0.1.4 - updating to match jQuery 1.7.2; **Please note that as of 0.1.4 underscore.deferred will be ALL LOWERCASE on
npm.** The camelcasing was a mistake from the outset, please update your
`package.json` appropriately.

MIT License.

[promise]: http://wiki.commonjs.org/wiki/Promises
[jquery-docs]: http://api.jquery.com/category/deferred-object/
[ender]: http://ender.no.de/

