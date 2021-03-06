# safe-json-globals

[![build status][1]][2] [![dependency status][3]][4]

<!-- [![browser support][5]][6] -->

Safely embed serialized JSON in a page as temporary global data. HTML tags are sanitized.

## Example for the server

```js
var JSONGlobals = require("safe-json-globals")

function (req, res) {
    getUser(req, res, function (userRecord) {
        var globalsMarkup = JSONGlobals({
          user: userRecord,
          potentialMaliciousContent: "</script><script>alert('hack')"
        })

        var html = "" // whatever html

        html += globalsMarkup

        res.end(html)
    })
}
```

## Example for the client

```js
var JSONGlobals = require("safe-json-globals/get")

var user = JSONGlobals("user")
```

## Installation

`npm install safe-json-globals`

## Contributors

 - Raynos
 - lxe

## MIT Licenced

  [1]: https://secure.travis-ci.org/lxe/safe-json-globals.png
  [2]: https://travis-ci.org/lxe/safe-json-globals
  [3]: https://david-dm.org/lxe/safe-json-globals.png
  [4]: https://david-dm.org/lxe/safe-json-globals
  [5]: https://ci.testling.com/lxe/safe-json-globals.png
  [6]: https://ci.testling.com/lxe/safe-json-globals
