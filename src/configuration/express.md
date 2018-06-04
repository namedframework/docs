Express Configuration
=====================

## config/server/express.js

*This file is called before loading routes and middlewares.*
```js
// sample configuration file
const bodyParser = require('body-parser');
const lusca = require('lusca');
const connectFlash = require('connect-flash');

const session = require('express-session');
const MongoStore = require('connect-mongo')(session);

// express app is passed as first argument
// also available at Framework.app
module.exports = function (app) {

  app.use( lusca.xframe('SAMEORIGIN') );
  app.use( lusca.xssProtection(true) );


  app.use( bodyParser.json() );
  app.use( bodyParser.urlencoded({ extended: true }) );

  app.use(session({
    resave: true,
    saveUninitialized: true,
    secret: Framework.config.session.secret,
    store: new MongoStore({
      url: Framework.config.session.uri || Framework.config.mongo.uri,
      autoReconnect: true,
    }),
  }));

  app.use( lusca.csrf() );

  app.use( connectFlash() );

};

```

## config/server/httperr.js
*This file is called after loading routes and middlewares.*
```js

// this can be used to handle errors
module.exports = function (app) {

  // 404 error
  app.use(function(req, res, next) {
    var err = new Error('Not Found');
    err.status = 404;
    next(err);
  });

  // default
  app.use(function(err, req, res, next) {
    var status = res.locals.status = err.status || 500;

    if (app.get('env') === 'development'){
      res.locals.error = err;
    }
    res.status(status).render('error');
  });

};

```
