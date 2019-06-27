# RequireJS

[TOC]

## What is RequireJS ?

- RequrieJS is a loader.
- RequireJS is a javaScript file and module loader.
- RequireJS is optimized for in-browser use.
- RequireJS also can be used in other JavaScript environments,like Rhino and Node.js.
- Using a modular script loader like RequireJS will improve the speed and qulity of your code.

## How to add RequireJS?

Directory layout of the project:

- www/

  + index.html

  + Js/
    * require.js
    * app.js
    * App/
    * Libs/

index.html: add `RequierJS`  to the `<head>` tag:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Demo</title>
    <script data-main="scripts/main" src="scripts/require.js"></script>
</head>
<body>
    <h1>Hello RequireJS</h1>
</body>
</html>
```

or add `RequireJS` to the end of the `<body>` tag:

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>Demo</title>
</head>
<body>
	<h1>Hello RequireJS</h1>
  <script data-main="scripts/main" src="scripts/require.js"></script>
</body>
</html>
```

Main.js

```JavaScript
console.log('Msg from main.js')
```

`data-main` : The data-main attribute is a special attribute that require.js will check to start script loading:This attribute tells require.js to load `scripts/main.js`  after `require.js`  loads.

```html
<!--Run index.html in browser and open console, you will see: `scripts/main.js` was loaded after `scripts/require.js` was loaded.-->
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>Demo</title>
  <script data-main="scripts/main" src="./scripts/require.js"></script>
	<script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="main" src="scripts/main.js"></script>
</head>
<body>
	<h1>Hello RequireJS</h1>
  <script data-main="scripts/main" src="scripts/require.js"></script>
</body>
</html>
```

Inside of `main.js` ,you can use requirejs() to load any other scripts you need to run. This ensures a single entry point, since the data-main script you specify is loaded asynchronously.

```javascript
requirejs(["helper/util"], function(util) {
    //This function is called when scripts/helper/util.js is loaded.
    //If util.js calls define(), then this function is not fired until
    //util's dependencies have loaded, and the util argument will hold
    //the module value for "helper/util".
});
```



