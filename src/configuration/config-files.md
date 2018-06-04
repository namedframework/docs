Configuration Files
===================

All exported objects by files in **config** directory are merged to **Framework.config**

```js
// config/mongo.js
module.exports.mongo = {
  uri: process.env.MONGODB_URI || 'mongodb://127.0.0.1:27017/namedframework-starter',
}
```

```js
// config/http.js
module.exports.http = {
  port: 8899,
}
```

**Default Configurations**

```js
{
  http: {
    port: 6789,
    public: 'public',
    viewEngine: 'pug',
    viewPath: 'views',
  }
}
```
