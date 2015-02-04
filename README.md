# umd
<img src="http://i.imgur.com/ypw29XY.png" align="right"/>

Universal Module Definition for use in automated build systems

 - simple synchronous wrapping of a string
 - optional wrapping of a "stream" with genuine streaming
 - `return` style module support
 - CommonJS support
 - prevents internal UMDs from conflicting

[![Build Status](https://img.shields.io/travis/ForbesLindesay/umd/master.svg)](https://travis-ci.org/ForbesLindesay/umd)
[![Dependency Status](https://img.shields.io/gemnasium/ForbesLindesay/umd.svg)](https://gemnasium.com/ForbesLindesay/umd)
[![NPM version](https://img.shields.io/npm/v/umd.svg)](http://badge.fury.io/js/umd)

## Source Format

In order for the UMD wrapper to work the source code for your module should `return` the export, e.g.

```javascript
function method() {
  //code
}
method.helper = function () {
  //code
}
return method;
```

For examples, see the examples directory.  The CommonJS module format is also supported by passing true as the second argument to methods.

## API

options:

 - `commonJS` (default: `false`) - If commonJS is `true` then it will accept CommonJS source instead of source code which `return`s the module.

### umd(name, [source], [options])

  The `name` should the the name of the module.  Use a string like name, all lower case with hyphens instead of spaces.

  If `source` is provided and is a string, then it is wrapped in umd and returned as a string.  If it is not provided, a duplex stream is returned which wraps the modules (see examples/build.js).

  Both commonJS and source are optional and can be provided in either order.

### umd.prelude(module, [options])

  return the text which will be inserted before a module.

### umd.postlude(module, [options])

  return the text which will be inserted after a module.

## Command Line

```
Usage: umd <name> <source> <destination> [options]

Pipe Usage: umd <name> [options] < source > destination

Options:

 -h --help     Display usage information
 -c --commonJS Use CommonJS module format
 ```

## License

  MIT
