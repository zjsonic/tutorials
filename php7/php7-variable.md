# Variable

## Superglobals

Superglobals are built-in variables that are always available in all scopes.

### $_POST

- `$_POST` is an array of variables passed to the current script via the HTTP POST method.
- `$_POST` is widely used to collect form data after submitting a HTML form with a post method.
- `$_POST` is also widely used to pass variables.

### $_GET

- `$_GET` is an array of variables passed to the current script via the URL parameters.
- `$_GET` is also widely used to collect form data after submitting a HTML form with a get method.
- `$_GET` can also collect hash data in the url.

### $_SERVER

`S_SERVER` is a global variable which holds information about:

- headers:
- paths:
- script locations:

The following table lists the most important fields that can go inside `$_SERVER`.

|Fields|Description|
|-|-|
|$_SERVER['PHP_SELF']| Returns the file name of currently excuting script.|
|$_SERVER['REQUEST_METHOD']| Returns the request method.|
|$_SERVER['HTTP_HOST']| Returns the Host header from the current request.|