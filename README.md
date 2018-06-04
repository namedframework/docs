Named Framework
=============

## Features

* Routes based on directory structure.
* Mongoose models
* Easy Configuration


## Built With
* [Express](http://expressjs.com/) - Fast, unopinionated, minimalist web framework for Node.js
* [Mongoose](http://mongoosejs.com/) - elegant mongodb object modeling for node.js

## Directory structure
```bash
├── config
│   ├── server
│   │   ├── express.js
│   │   ├── httperr.js
│   │   ├── middlewares.js
│   ├── local.js
│   ├── ... other config files
├── lib
│   ├── utils
│   │   ├── index.js
│   │   ├── ... other utils
├── public/
├── server/
│   ├── boot/
│   ├── middlewares/
│   ├── models/
│   ├── plugins/
│   ├── routes/
├── app.js
├── nodemon.json (if using nodemon)
├── package.json
└── .gitignore
```
