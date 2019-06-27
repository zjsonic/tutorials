# WebPack

## What is the webpack
Webpack is a static module bundler for modern js app. Webpack builds a dependency graph which maps every models your project needs.Webpack gendrates one or more bundlers.Webpack is used to compile JavaScript modules. 

- bundle your scripts
- bundle your images
- bundle your styles
- bundle your assets

## Install webpack and webpack-cli

```bash
mkdir webpack-demo
cd webpack-demo
npm init -y
npm install webpack --save-dev
npm install webpack-cli --save-dev
webpack src/index.js -o dist/bundle.js # bundle your source code with the entry as index.js and the output bundle file will have a path of dist
```


## Entry

Entry indicates: webpack should use this module to begin building its dependency graph.  

- By default, its value is `./src/index.js`

## Output

Output property tells webpack:

- where to emit the bundles.
- how to name these files

## Loaders

Loaders allow webpack to process other types of files.
Loaders convert other types of files into valid modules.

## webpack-dev-server

installation

```bash
npm install webpack-dev-server --save-dev
```

resutls

```bash
Project is running at http://localhost:8080/
ℹ ｢wds｣: webpack output is served from /
ℹ ｢wds｣: Content not from webpack is served from /Users/zj/my-projects/learn/learn-webpack
```