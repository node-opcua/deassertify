# Deassertify

  Browserify transform to comment assert statements out of your code.



For example.js:

```javascript
function foo(a) {
  assert(a >= 0, " expecting a positive number");
  return Math.sqrt(a);
}
```

then on the command line:

     browserify -t deassertify example.js > bundle.js

You can also pass in the argument `nobundle` to prevent the assert package
from being added to your bundle.

     browserify -t [deassertify --nobundle] example.js > bundle.js

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
