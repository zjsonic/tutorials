# Global Objects


**Global Objects** refer to objects in the global scope.

**Global Object** can be accessed using the `this` operator in the global scope.

**Global Scope**: consits of the properties of the global object,including inherited properties,if any.

- Number()
- String()
- Boolean()
- Function()
- Array()
- Object()
- Error()


## 参考
- [http://www.ecma-international.org/ecma-262/5.1/#sec-15.2.4.2](http://www.ecma-international.org/ecma-262/5.1/#sec-15.2.4.2)

## Number()
**用途** :



## Object.prototype.toString ( )

Object.prototype.toString ( )
When the toString method is called, the following steps are taken:

- If the this value is undefined, return "[object Undefined]".
- If the this value is null, return "[object Null]".
- Let O be the result of calling ToObject passing the this value as the argument.
- Let class be the value of the [[Class]] internal property of O.
- Return the String value that is the result of concatenating the three Strings "[object ", class, and "]".
