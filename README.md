<<<<<<< HEAD
mongo-interface
=============

Web-based MongoDB admin interface written with Node.js and express - (Latest Bootstrap 3 UI)

Original Source below :

[![Build Status](https://secure.travis-ci.org/andzdroid/mongo-express.png?branch=master)](http://travis-ci.org/andzdroid/mongo-express) - Master (stable) branch

[![Build Status](https://secure.travis-ci.org/andzdroid/mongo-express.png?branch=develop)](http://travis-ci.org/andzdroid/mongo-express) - Develop branch


Features
--------

Current features:

* Connect to multiple databases
* Connect and authenticate to individual databases
* Authenticate as admin to view all databases
* Database blacklist/whitelist
* View/add/rename/delete collections
* View/add/update/delete documents
* Use BSON data types in documents

Planned features:

* Support for replica set connections
* Web-based command-line interface
* Site authentication
* REST interface


Limitations
-----------

* Documents must have `document._id` property to be edited
* No GridFS support (might become a planned feature)
* Binary BSON data type not tested

JSON documents are parsed through a javascript virtual machine, so **the web
interface can be used for executing malicious javascript on a server**.

**mongo-interface should only be used privately for development purposes**.


Screenshots
-----------

<img src="http://i.imgur.com/LCqfCWEl.png?1" title="Viewing documents in a collection" />

These screenshots are updated with bootstrap 3 from version 0.11.0.


Usage
-----

**To install:**

    npm install mongo-express

Or if you want to install a global copy:

    npm install -g mongo-express

**To configure:**

Copy or rename `config.default.js` into a new file called `config.js`.

Fill in your MongoDB connection details, and any other options you want to change.

**To run:**

    node app

**To use:**

Visit `http://localhost:8081` or whatever URL/port you entered into your config.


BSON Data Types
---------------

The following BSON data types are supported in the mongo-express document editor/viewer.

**Native Javascript Types**

Strings, numbers, lists, booleans, null, etc.

All numbers in Javascript are 64-bit floating points.

**ObjectID/ObjectId**

    ObjectID()

Creates a new Object ID type.

    ObjectID(id)

Use Object ID with the given 24-digit hexadecimal string.

**ISODate**

    ISODate()

Creates a new ISODate object with current time.

`new Date()` can also be used (note the `new` keyword there).

    ISODate(timestamp)

Uses ISODate object with the given timestamp.

**DBRef/Dbref**

    DBRef(collection, objectID)

    DBRef(collection, objectID, database)

Object ID is the ID string, not the ObjectID type.

The database value is optional.

**Timestamp**

    Timestamp()

Creates a new Timestamp object with a value of 0.

    Timestamp(time, ordinal)

Example: `Timestamp(ISODate(), 0)`.

See [http://www.mongodb.org/display/DOCS/Timestamp+data+type](http://www.mongodb.org/display/DOCS/Timestamp+data+type) for more info about the Timestamp data type.

**Code**

    Code(code)

Code can be a native Javascript function, or it can be a string.

Specifying a scope/context is not supported.

**MinKey**

    MinKey()

**MaxKey**

    MaxKey()

**Symbol**

    Symbol(string)

---

Not tested:

* Binary/BinData

Here is an example of a document which can be read/edited in mongo-express:

    {
      "_id": ObjectID(), // or ObjectId()
      "dates": {
        "date": ISODate("2012-05-14T16:20:09.314Z"),
        "new_date": ISODate(),
        "alternative": new Date()
      },
      "bool": true,
      "string": "hello world!",
      "list of numbers": [
        123,
        111e+87,
        4.4,
        -12345.765
      ],
      "reference": DBRef("collection", "4fb1299686a989240b000001"),
      "ts": Timestamp(ISODate(), 1),
      "minkey": MinKey(),
      "maxkey": MaxKey(),
      "func": Code(function() { alert('Hello World!') }),
      "symbol": Symbol("test")
    }

=======
# mongo-interface
MongoDB interface for database
>>>>>>> 6539dff4e8cd29d1c168ca427a17ad04998ae3b9
