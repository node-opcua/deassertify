# Deassertify

  Browserify transform that comment assert statement out of your code.



For example.js:

```javascript
function foo(a) {
  assert(a >= 0, " expecting a positive number");
  return Math.sqrt(a);
}
```

then on the command line:

     browserify -t deassertify example.js > bundle.js

or with the api:

```javascript
var browserify = require("browserify")
 , fs = require("fs")

var b = browserify("example.js")
b.transform("deassertify")

b.bundle().pipe(fs.createWriteStream("bundle.js"))
```

the bundle file output is:

```javascript
function foo(a) {
  //-- assert(a >= 0, " expecting a positive number");
  return Math.sqrt(a);
}
```

Licence: MIT
