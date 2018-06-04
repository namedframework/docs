Creating Routes
===============

Routes are loaded from **server/routes/** directory and route path follows the directory structure.

* **server/routes/index.js** routes to **/**
* **server/routes/news/by/author.js** routes to **/news/by/author**

## Get Route
```js
// server/routes/index.js
module.exports = {
  // get route for /
  get: function (req, res, next) {
    res.render('index');
  },
};
```

## Post Route
```js
// server/routes/login.js
module.exports = {
  // get route for /login
  get: function (req, res, next) {
    res.render('login');
  },

  // post route for /login
  post: function (req, res, next) {
    // check db user
    Framework.models.User.findOne({email: req.body.email})
    .lean()
    .exec(function (err, user) {
      // check if exists
      // check password
      // redirect
      res.redirect('/dashboard');
    });
  },
};
```

## Other routes
```js
module.exports = {
  put: (req, res, next) => {},
  delete: (req, res, next) => {},
  patch: (req, res, next) => {},
};
```
