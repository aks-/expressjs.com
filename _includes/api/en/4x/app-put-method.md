<h3 id='app.put.method'>app.put(path, callback [, callback ...])</h3>

Routes HTTP PUT requests to the specified path with the specified callback functions.
For more information, see the [routing guide](/guide/routing.html).

You can provide multiple callback functions that behave just like middleware,
except that these callbacks can invoke `next('route')` to bypass the
remaining route callback(s). You can use this mechanism to impose pre-conditions on
a route, then pass control to subsequent routes if there's no reason to proceed with
the current route.

```js
app.put('/', function (req, res) {
  res.send('PUT request to homepage');
});

// path could be array of strings
app.put(['/foo/bar', '/other/bar'], function (req, res) {
  res.send('PUT request to any of above path');
});

// path could be regex
app.put(/^\/yellboom(er|s)?$/, function (req, res) {
  res.send('PUT request to page that starts with startswithboom');
});

// path could be array of regex
app.put([/^\/yellboom(er|s)?$/, /^\/ab(cd)?e$/], function (req, res) {
  res.send('PUT request to page that matches any of above regex path');
});
```
