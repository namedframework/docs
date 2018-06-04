Create New Project
==================

Create project directory
```bash
$ mkdir starter
```

NPM Init
```bash
$ cd starter
$ npm init
```

Install NamedFramework
```bash
$ npm install --save namedframework
```

Create app.js
```js
// require Framework
const Framework = require('namedframework');

// start Framework
Framework.init();

```

Start
```
$ nodemon app.js
Mongodb connection uri not found, proceding without db support.
✓ App is running at http://localhost:6789 in development mode
  Press CTRL-C to stop
```
