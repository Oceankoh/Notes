
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

Line: 168-178
```js
if (methodToCall.constructor &&	
	methodToCall.constructor.name === "AsyncFunction"
	) {
	const result = await methodToCall(socket, params);
	callback(null, result);
} else {
	methodToCall(socket, params, (err, result) => {
		callback(err ? { message: err.message } : null, result);
	});
}
```

Example websocket message to invoke function:
```
427["categories.loadMore",{"cid":2,"after":1,"direction":1,"query":{},"categoryTopicSort":"newest_to_oldest"}]
```

#### Conditions
	
##### 

##### 