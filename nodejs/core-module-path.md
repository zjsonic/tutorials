# Path

## What is a path module

Path module provides utilities for working with file paths or directory paths. It can be accessed using:

```js
const path = require('path)

```

## path.join([path])

`path.join()` method joins all given path segments together.

```js
path.join('/foo', 'bar', '/baz/asdf', 'quux', '...')
path.join(__dirname, './src/index.js')
```

- `[path]`: a sequence of path sequence. must be a string.
- `__dirname`: 
