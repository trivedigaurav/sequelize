# Sequelize [![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/sequelize/sequelize/trend.png)](https://bitdeli.com/free "Bitdeli Badge") [![Build Status](https://secure.travis-ci.org/sequelize/sequelize.png)](http://travis-ci.org/sequelize/sequelize) [![Dependency Status](https://david-dm.org/sequelize/sequelize.png)](https://david-dm.org/sequelize/sequelize) [![Flattr this](http://api.flattr.com/button/flattr-badge-large.png)](http://flattr.com/thing/1259407/Sequelize) #

MySQL, MariaDB, PostgresSQL, and SQLite Object Relational Mapper (ORM) for [node](http://nodejs.org).

## Important Notes ##

### 2.0.0 ###

There is a parallel "branch" of the project, released as `2.0.0-alphaX` in NPM. All those releases are based on the master
and will get all the changes of the master. However, `2.0.0` will contain backwards compatibility breaking changes. Check the
changelog of the branch: https://github.com/sequelize/sequelize/blob/milestones/2.0.0/changelog.md

### 1.6.0 ###

- We changed the way timestamps are handled. From v1.6.0 on timestamps are stored and loaded as UTC.
- Support for synchronous migrations has been dropped. `up` and `down` methods in migrations do have a third parameter which is the callback parameter. Pass an error or an error message as first parameter to the callback if something went wrong in the migration.

## Blogposts/Changes ##
- [v1.6.0](http://blog.sequelizejs.com/post/46949108134/v1-6-0-eager-loading-support-for-enums-decimals-and) Eager loading, support for enums, decimals and bigint, performance improvements …
- [v1.4.1](http://blog.sequelizejs.com/post/24403298792/changes-in-sequelize-1-4-1): deprecation of node < 0.6, logging customization, ...
- [v1.4.0](http://blog.sequelizejs.com/post/24345409723/changes-in-sequelize-1-4-0): postgresql, connection pooling, ...
- [v1.3.0](http://blog.depold.com/post/15283366633/changes-in-sequelize-1-3-0): migrations, cross-database, validations, new listener notation, ...
- [v1.2.1](http://blog.depold.com/post/12319530694/changes-in-sequelize-1-2-1): changes some defaults and some interfaces
- [v1.0.0](http://blog.depold.com/post/5936116582/changes-in-sequelize-1-0-0): complete rewrite

## Features ##

- Schema definition
- Schema synchronization/dropping
- Easy definition of class/instance methods
- Instance saving/updating/dropping
- Asynchronous library
- Associations
- Importing definitions from single files
- Promises
- Hooks/callbacks/lifecycle events

## Documentation and Updates ##

You can find the documentation and announcements of updates on the [project's website](http://www.sequelizejs.com).
If you want to know about latest development and releases, follow me on [Twitter](http://twitter.com/sdepold).
Also make sure to take a look at the examples in the repository. The website will contain them soon, as well.

- [Documentation](http://www.sequelizejs.com)
- [Twitter](http://twitter.com/sdepold)
- [IRC](http://webchat.freenode.net?channels=sequelizejs)
- [Google Groups](https://groups.google.com/forum/#!forum/sequelize)
- [XING](https://www.xing.com/net/priec1b5cx/sequelize) (pretty much inactive, but you might want to name it on your profile)

## Running Examples
Instructions for running samples are located in the [example directory](https://github.com/sequelize/sequelize/tree/master/examples). Try these samples in a live sandbox environment:

<a href="https://runnable.com/sequelize" target="_blank"><img src="https://runnable.com/external/styles/assets/runnablebtn.png"></a>

## Roadmap

A very basic roadmap. Chances aren't too bad, that not mentioned things are implemented as well. Don't panic :)

### 1.7.0
- ~~Check if lodash is a proper alternative to current underscore usage.~~
- ~~Transactions~~
- Associations of not yet saved objects: [#864](https://github.com/sequelize/sequelize/issues/864)
- Support for update of tables without primary key
- ~~MariaDB support~~
- ~~Support for update and delete calls for whole tables without previous loading of instances~~ Implemented in [#569](https://github.com/sequelize/sequelize/pull/569) thanks to @optiltude
- Eager loading of nested associations [#388](https://github.com/sequelize/sequelize/issues/388)
- ~~Model#delete~~ (renamed to [Model.destroy()](http://sequelizejs.com/documentation#instances-destroy))
- ~~Validate a model before it gets saved.~~ Implemented in [#601](https://github.com/sequelize/sequelize/pull/601), thanks to @durango
- ~~Move validation of enum attribute value to validate method~~ Implemented in [#894](https://github.com/sequelize/sequelize/pull/894) thanks to @durango
- ~~BLOB~~  [#842](https://github.com/sequelize/sequelize/pull/842), thanks to @janmeier
- ~~Support for foreign keys~~ Implemented in [#595](https://github.com/sequelize/sequelize/pull/595), thanks to @optilude
- Support for socket paths. [#982](https://github.com/sequelize/sequelize/issues/982)

### 1.7.x
- Complete support for non-id primary keys

### 1.8.0
- API sugar (like Model.select().where().group().include().all())
- Schema dumping
- ~~enum support~~
- attributes / values of a dao instance should be scoped

### 2.0.0
- ~~save datetimes in UTC~~
- encapsulate attributes if a dao inside the attributes property
- ~~add getters and setters for dao~~ Implemented in [#538](https://github.com/sequelize/sequelize/pull/538), thanks to iamjochem
- add proper error message everywhere
- refactor validate() output data structure, separating field-specific errors
  from general model validator errors (i.e.
  `{fields: {field1: ['field1error1']}, model: ['modelError1']}` or similar)


## Collaboration 2.0 ##

I'm glad to get pull request if any functionality is missing or something is buggy. But _please_ ... run the tests before you send me the pull request.

Still interested? Coolio! Here is how to get started:

### 1. Prepare your environment ###

Here comes a little surprise: You need [Node.JS](http://nodejs.org). In order to be
a productive developer, I would recommend the latest v0.8. Also I usually recommend
[NVM](https://github.com/creationix/nvm).

Once Node.JS is installed on your computer, you will also have access to the lovely
Node Package Manager (NPM).

### 2. Database... Come to me! ###

First class citizen of Sequelize was MySQL. Over time, Sequelize began to
become compatible to SQLite and PostgreSQL. In order to provide a fully
featured pull request, you would most likely want to install of them. Give
it a try, it's not that hard.

If you are too lazy or just don't know how to get this work,
feel free to join the IRC channel (freenode@#sequelizejs).

For MySQL and PostgreSQL you'll need to create a DB called `sequelize_test`.
For MySQL this would look like this:

```console
$ echo "CREATE DATABASE sequelize_test;" | mysql -uroot
```

**CLEVER NOTE:** your local MySQL install must be with username `root`
  without password. If you want to customize that just hack in the
  tests, but make sure to don't commit your credentials, we don't want
  to expose your personal data in sequelize codebase ;)

**AND ONE LAST THING:** Once `npm install` worked for you (see below), you'll
get SQLite tests for free :)


### 3. Install the dependencies ###

Just "cd" into sequelize directory and run `npm install`, see an example below:

```console
$ cd path/to/sequelize
$ npm install
```

### 4. Run the tests ###

Right now, the test base is split into the `test` folder (which contains the
lovely [Mocha](http://visionmedia.github.io/mocha/) tests).

As you might haven't installed all of the supported SQL dialects, here is how
to run the test suites for your development environment:

```console
$ # run all tests at once:
$ make all

$ # run the buster specs for mysql:
$ make mysql

$ # run the buster specs for sqlite:
$ make sqlite

$ # run the buster specs for postgresql:
$ make pgsql

$ # alternatively you can pass database credentials with $variables when testing
$ DIALECT=dialect SEQ_DB=database SEQ_USER=user SEQ_PW=password make test
```

### 5. That's all ###

Just commit and send pull requests.
Happy hacking and thank you for contributing.
Ah and one last thing: If you think you deserve it, feel free to add yourself to the
`package.json`. Also I always look for projects which are using sequelize. If you have
one of them, drop me a line!

### 6. Some words about coding style ###

As people are regularly complaining about missing semi-colons and strangely formatted
things, I just want to explain the way I code JavaScript (including Sequelize
... obviously). I won't reject any pull-request because of having a different code
style than me but it would be good to have a consistent way of coding in the whole
project. Here are my rules of thumb:

- No semi-colons. Where possible I try to avoid semi-colons. Please don't discuss this topic with me. Thanks.
- Curly braces for single line if blocks. I always add curly braces to if blocks. Same for loops and other places.
- Spacing. Indentation = 2 spaces. Also I add a lot of spaces where possible. See below.
- Anonymous functions over names functions. Usually I declare a function and assign it to a variable: `var foo = function() {}`
- Variable declarations. If multiple variables are defined, I use a leading comma for separation.
- Camelcased variable names. No underscores.
- Make sure that key is in objects when iterating over it. See below.

#### 6.1. Spaces ####

Use spaces when defining functions.

```js
function(arg1, arg2, arg3) {
  return 1
}
```

Use spaces for if statements.

```js
if (condition) {
  // do something
} else {
  // something else
}
```

#### 6.2. Variable declarations ####

```js
var num  = 1
  , user = new User()
  , date = new Date()
```

#### 6.3. For-In-loops ####

```js
for (var key in obj) {
  if (obj.hasOwnProperty(key)) {
    console.log(obj[key])
  }
}
```

#### 6.4. JSHint options ####

```js
{
  "globals": {
    "spyOn": false,
    "it": false,
    "console": false,
    "describe": false,
    "expect": false,
    "beforeEach": false,
    "waits": false,
    "waitsFor": false,
    "runs": false
  },
  "camelcase": true,
  "curly": true,
  "forin": true,
  "indent": 2,
  "unused": true,
  "asi": true,
  "evil": false,
  "laxcomma": true,
  "es5": true
}
```
