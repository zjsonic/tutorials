[TOC]

# Path

## What is a path module

Path module provides utilities for working with file paths or directory paths. It can be accessed using:

```js
const path = require('path)
```

## Windows vs POSIX

The default operation of the `path` module varies based on the operating system on which a Node.js application is running. Specifically, when running on a Window operating system, the `path` module will assume that window-style paths are being used. So using `path.basename()` might yield different results  on POSIX and windows:

On POSIX:

```javascript
path.basename('C:\\temp\\myfile.html');
// Returns: 'C:\\temp\\myfile.html'
```

On Windows:

```javascript
path.basename('C:\\temp\\myfile.html');
// Returns: 'myfile.html'
```

## path.basename(path[,ext])



## path.join([path])

`path.join()` method joins all given path segments together.

```js
path.join('/foo', 'bar', '/baz/asdf', 'quux', '...')
path.join(__dirname, './src/index.js')
```

- `[path]`: a sequence of path sequence. must be a string.
- `__dirname`: 
