Mongoose Plugins
===============

Mongoose plugins located at **server/plugins/mongoose/** are loaded as global plugins.

```js
// example plugin
// server/plugins/mongoose/timestamp.js
module.exports = function (schema, options) {
  schema.add({ createdAt: Date });
  schema.add({ updatedAt: Date });

  schema.pre('update', function() {
    this.update({},{ $set: { updatedAt: new Date() } });
  });

  schema.pre('findOneAndUpdate', function() {
    this.update({},{ $set: { updatedAt: new Date() } });
  });

  schema.pre('save', function (next) {
    if (this.isNew) {
      this.createdAt = new Date();
    }
    this.updatedAt = new Date();

    next();
  });

};

```
