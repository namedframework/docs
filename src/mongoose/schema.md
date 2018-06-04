Mongoose Schema
===============

Mongoose schema are declared **server/models/** and are loaded recursively at **Framework.models[filename]**.

Below declared models are accessible  at:
* **Framework.models.User**
* **Framework.models.NewsCategory**
* **Framework.models.News**

```js
// server/models/User.js
module.exports = {
  options: {
    // mongoose options here
    timestamps: true
    // ...
  },
  schema: {
    // define schema here
    name: String,
    email: {
      type: String,
      required: true,
      trim: true,
      unique: true,
      match: /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/
    },
    password: String,
    gender: {
      type: String,
      enum: ["Male", "Female", "Other"]
    },
    // .....
  },
  // define mongoose statics
  statics: {
    encryptPassword: () => {},
    validatePassword: () => {},
  },
  // virtuals
  virtuals: {},

  // methods
  methods: {},

  // pre / post hooks
  // ['init', 'validate', 'save', 'remove']
  pre: {},
  post: {},

  // queryHelpers
  queryHelpers: {},

  // indexes
  queryHelpers: {},

};
```

```js
// server/models/news/NewsCategory.js
module.exports = {
  schema: {
    name: String,
    description: String,
    image: String,
  }
};
```

```js
// server/models/news/News.js
module.exports = {
  schema: {
    user: {
      type: Framework.mongoose.Schema.Types.ObjectId,
      model: 'User',
    },
    category: {
      type: Framework.mongoose.Schema.Types.ObjectId,
      model: 'NewsCategory',
    },
    title: String,
    description: String,
    content: String,
    image: String,
  }
};
```
