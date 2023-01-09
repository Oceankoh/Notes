
## Prototype Pollution

### Object: `Namespaces`

### `before` function called on Namespaces

File: `src/socket.io/index.js`
Line: 155-157
```js
if (Namespaces[namespace].before) {
	await Namespaces[namespace].before(socket, eventName, params);
}
```

#### Conditions

##### Control `namespace`

File: `src/socket.io/index.js`
Line: 123-124
```js
async function onMessage(socket, payload) {
...
	const eventName = payload.data[0];
...
	const parts = eventName.toString().split('.');
	const namespace = parts[0];
```

##### Pollute`Object.Prototype.before`
???

##### Invoke with ???

### `methodToCall` contructed from eventName

File: `src/socket.io/index.js`
Line: 123-130
```js
const parts = eventName.toString().split('.');
const namespace = parts[0];
const methodToCall = parts.reduce((prev, cur) => {
	if (prev !== null && prev[cur]) {
		return prev[cur];
	}
	return null;
}, Namespaces);
```

#### Conditions

##### 