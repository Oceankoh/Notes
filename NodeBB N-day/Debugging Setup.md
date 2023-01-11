### NodeBB internals

Source code contains `nodebb` exectuable which is really just a node script that calls the cli module. Program forks a child process is responisble for setup. Once the application has been setup, it forks another child process to run the server. In order to debug the main application, we need to attach the debugger to these child processes. To do so, modify the source code as follows

File: `loader.js:128-132`
```js
const worker = fork(appPath, args, {
	silent: silent,
	env: process.env,
	execArgv: ['--inspect=0.0.0.0']
});
```

File:`docker-compose.yml`
```yml
version: '3.5'

services:
  node:
    build: .
    restart: unless-stopped
    depends_on:
      - db
    ports:
      - 4567:4567 # expose app
      - 9229:9229 # expose debugging port

  db:
    image: mongo:bionic
    restart: unless-stopped
    ports:
      - 27017:27017
    environment:
      - MONGO_INITDB_ROOT_USERNAME="root"
      - MONGO_INITDB_ROOT_PASSWORD="root"
    volumes:
      - mongo:/data/db

volumes:
  mongo:
```
