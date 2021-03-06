# gulp-json-server [![Build Status](https://travis-ci.org/GrafGenerator/gulp-json-server.svg?branch=master)](https://travis-ci.org/GrafGenerator/gulp-json-server) [![npm version](https://badge.fury.io/js/gulp-json-srv.svg)](https://badge.fury.io/js/gulp-json-srv)

Wrapper for [json-server](https://github.com/typicode/json-server).

**Important!** Version 1.0.0 released and contains breaking changes, see this page for new API, and [examples of usage](SAMPLES.md).

## Install

```
$ npm install --save-dev gulp-json-srv
```


## Usage
```js
var gulp = require("gulp");
var jsonServer = require("gulp-json-srv");

var server = jsonServer.create();

gulp.task("start", function(){
    return gulp.src("data.json")
        .pipe(server.pipe());
});
```

See [samples](SAMPLES.md) for more information about usage of plugin.


## API

### Options

| Options | Default value | Description |
|:---|:---|:---|
|`baseUrl`|`null`|The base URL for server API.|
|`cumulative`|`false`|Controls when to merge files from different `pipe()` calls (i.e. two pipelines execution.)|
|`cumulativeSession`|`true`|Controls when to merge files in one `pipe()` call (i.e. one pipeline execution.). If not, then only last file passed to plugin will form the DB state.|
|`customRoutes`|`null`|A key-value pairs of custom routes that should be applied to server. Each value should be the object with `method` and `handler` properties, describing HTTP method and handler of custom route respectively.|
|`debug`|`false`|If true, produces extra output in console, useful for debug.|
|`id`|`"id"`|Identity property name of objects. Changing this allows to imitate MongoDB's `_id` f.e.|
|`port`|`3000`|Port number on which json-server will listen.|
|`rewriteRules`|`null`|A key-value pairs of rewrite rules that should be applied to server.|
|`static`|`null`|If specified and not null, sets the static files folder and lets json-server serve static files from that folder.|

**Important:** Note that `cumulative` and `cumulativeSession` options could be specified in `options` object, passed to `pipe()` method and they will override one set at server level.

### Methods
| Method | Description |
|---|---|
|`kill(callback)`|Immediately stops the server and closes all opened connections. If `callback` is provided, it will be called once server stopped.|
|`pipe(options)`|Provides stream trasformation for gulp pipeline. Passing `'options'` to this method allows to override options, set at server level (currently `cumulative` and `cumulativeSession` are overridable). |

## Links

* [SAMPLES.md](SAMPLES.md) - more examples of usage
* [CHANGELOG.md](CHANGELOG.md)
* [CONTRIBUTING.md](CONTRIBUTING.md) - info for contributors

## License

MIT © 2016 Nikita Ivanov
