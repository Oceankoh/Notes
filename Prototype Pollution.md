## Sources

Occurs when recursive merge 

## Sinks
When a value from an object is referenced for example 

```js
let foo = {}
foo.bar
```

Javascript looks for the value of bar in the object foo, and it's prototype. Therefore, setting the value of `bar` in the `Object` prototype will also result in the same value being returned in `foo.bar`, if it is not explicitly defined. 

```js
let foo = {}
Object.prototype.bar = 'value'
foo.bar // returns 'value'
foo.bar = 'overwritten'
Object.prototype.bar === foo.bar // returns false
```
![[Pasted image 20221208190042.png]]

## Prevention

### Node