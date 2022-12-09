# Inheritiance

When an emtpy object, string or number is defined, there are already existing properties to that variable. 2 such examples are the `constructor` function and the `__proto__` object. 

## Constructor Function

"constructor" is a magic property that returns the function used to create the object. What's good to note is that on every constructor there is the property "prototype" which poitns to the prototype of the class. 

```js
function Test(){};
Test.prototype.randomFunction = function (){}
objA.constructor.prototype // returns Test.prototype.randomFunction
```

## `__proto__` Object

 `__proto__` is a magic property that reutns the "prototype" of the class of the object. While this property is not standard in the Javascript language, it's fully supported in the NOdeJS environment. What's good to note about this property is that it's imoplmeneted as a getter/setter proprety which invokes getPrototypeOf/setPrototypeOf on read/write. So wassigning a new calue to the property "__proto__" doesn't shadow the inherited value defined on the prototype. The only way to shadow it involves using "object.defineProperty".

