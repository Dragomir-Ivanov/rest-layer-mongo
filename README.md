# REST Layer MongoDB backend [![godoc](http://img.shields.io/badge/godoc-reference-blue.svg?style=flat)](https://godoc.org/github.com/rs/rest-layer-mongo) [![license](http://img.shields.io/badge/license-MIT-red.svg?style=flat)](https://raw.githubusercontent.com/rs/rest-layer-mongo/master/LICENSE) [![build](https://img.shields.io/travis/rs/rest-layer-mongo.svg?style=flat)](https://travis-ci.org/rs/rest-layer-mongo)

This REST Layer resource storage backend stores data in a MongoDB cluster using [mgo](https://godoc.org/labix.org/v2/mgo).

## Usage

```go
import "github.com/rs/rest-layer-mongo"
```

Create a mgo master session:

```go
session, err := mgo.Dial(url)
```

Create a resource storage handler with a given DB/collection:

```go
s := mongo.NewHandler(session, "the_db", "the_collection")
```

Use this handler with a resource:

```go
index.Bind("foo", resource.NewResource(foo, s, resource.DefaultConf)
```

You may want to create a many mongo handlers as you have resources as long as you want each resources in a different collection. You can share the same `mgo` session across all you handlers.