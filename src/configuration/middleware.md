Middleware Configuration
=========================

## config/server/middlewares.js
Use this file to define middleware for routes.

```js
// example
module.exports = {
  // actual file at server/middlewares/setLocals
  // use array for multiple middlewares
  '/': ['setLocals', 'getLoginStatus'],

  // actual file at server/middlewares/user/isAuthenticated
  '/user': 'user/isAuthenticated',

  // here special is passed as function parameter
  '/user/special': 'user/isAllowed special',

  // actual file at server/middlewares/admin/isAuthenticated
  '/admin': 'admin/isAuthenticated',
};

```

## Declaring middleware
Create middleware file at **server/middlewares/**.

```js
// server/middlewares/setLocals.js
module.exports = function (req, res, next) {
  // url
  res.locals.url = req.originalUrl;

  // flash messages
  res.locals.flash = {
    info: req.flash('info'),
    error: req.flash('error'),
    warning: req.flash('warning'),
    success: req.flash('success'),
  };
  return next();
};

```

## Declaring closure middleware

```js
// server/middlewares/user/isAllowed.js
module.exports = {
  run: true,
  middleware: function (name) {
    return function (req, res, next) {
      switch (name) {
        case "special":
          return !!req.user.isSpecial;
          break;
        default:
          return false;
      }
    }
  },
};

```
