[TOC]

# CommonJS vs AMD vs RequireJS vs ES6 Modules

## About JavaScript Modules

JavaScript Modules refers to a small unit of independent, reusable code.

- Each module has distinct functionality.
- JavaScript Modules System allows modules to be added, removed without disrupting the system.

All of these module systems have one thing in common: they allow you to export and import stuff.

## CommonJS

`CommonJS` is a project with the goal to establish conventions on ecosystem for javascript outside the web browser, such as web server, desktop and so on.

`CommonJS` came up with a separate approach to interact with the module system using the key words `exports` and `require`.

- Require(): Require is a function used to import function from another module.
- Exports: Exports is an object where any function put into it will get exported.

## NodeJS

NodeJS is heaviy influencely by CommonJS specification. The major difference arises in the `exports` object.

- NodeJS: uses `module.exports` as the object to get exported.
- CommonJS: uses just the `exports` variable to get exported.

## AMD

amd

## RequireJS

requirejs

## ES6 Modules

Es6 modules

## References

[https://medium.com/computed-comparisons/commonjs-vs-amd-vs-requirejs-vs-es6-modules-2e814b114a0b](https://medium.com/computed-comparisons/commonjs-vs-amd-vs-requirejs-vs-es6-modules-2e814b114a0b)

