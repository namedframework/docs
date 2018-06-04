Local Configuration
===================

## config/local.js
Use this file to override values in other configuration files.
**Add this file to .gitignore**

```js
// Example
module.exports = {
  http: {
    port: '8899',
  },
  mongo: {
    uri: "mongodb://localhost/local-test-db",
  },
  recaptcha: {
    secret: "top-secret",
    sitekey: "not-so-secret",
  },
  // ...... many more
};
```
