Route Configuration
===================

## Route Parameters
```js
// server/routes/news/details.js
module.exports = {
  _config: {
    params: "id", // /news/details/:id
    params: ["slug", "id"], // /news/details/:slug/:id
  },

  get: function (req, res, next) {
    // get news from db
    res.render('news/details');
  },
};
```

## Route Middlewares
```js
// server/routes/news/details.js
module.exports = {
  _config: {
    params: ["slug", "id"], // /news/details/:slug/:id
    middleware: 'news/isAllowed view_news', // route specific, array for multiple
  },

  get: function (req, res, next) {
    // get news from db
    res.render('news/details');
  },
};
```

## Method specific Middlewares
```js
// server/routes/news/details.js
module.exports = {
  _config: {
    params: ["slug", "id"], // /news/details/:slug/:id
    middleware: {
      all: 'news/isAllowed view_news',
      get: ['news/getTopNews', 'news/getPopularNews'],
      post: ['news/isAllowedToComment'],
    }
  },

  get: (req, res, next) => {},
  post: (req, res, next) => {},
};
```

## Override route url
```js
// server/routes/news/details.js
module.exports = {
  _config: {
    params: 'id', // params will not work if url is present
    url: "/news/:newsId/comment/:commentId", // provide full url with params
  },

  get: function (req, res, next) {
    // get news from db
    res.render('news/details');
  },
};
```
