Boot Scripts
============

* JS files located at **server/boot/** that export function are called once server boots up.
* Useful for scheduling cron jobs.
* boot scrips must run callback function received as first argument
* **this** points to Framework 

```js
// server/boot/001-test.js
module.exports = function (callback) {
  // const Framework = this;
  // Also Framework is globally available
  console.log('Server started at %s', new Date());
  callback();
};
```
