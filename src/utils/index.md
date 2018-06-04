Utils
======

* JS files located at **lib/utils/** can be accessed at **Framework.utils**.
* If file exports object, it is merged with **Framework.utils**.
* If function is exported, filename is used as key **Framework.utils[filename]**.

```js
// server/boot/001-test.js
module.exports = function (callback) {
  // const Framework = this;
  // Also Framework is globally available
  console.log('Server started at %s', new Date());
  callback();
};
```
