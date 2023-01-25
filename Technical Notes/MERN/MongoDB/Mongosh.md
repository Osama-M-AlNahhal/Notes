
### basic
start the mongodb shell
```mongosh
mongosh
```

show a list of databases
```mongosh
show dbs
```

switch to a certain database 
```mongosh
use dbname
```

clear screen
```mongosh
cls
```

show the current database name
```mongosh
db
```

show a list of collections
```mongosh
show collections
```

creating, editing and accessing variables
```mongosh
var var1 = "value"

var1 = "newValue"

var1
```

list of all available commands
```mongosh
help
```

exit the mongosh
```mongosh
exit
```

insert a document into a collection
```mongosh
db.collectionName.insertOne({attr1: "value", attr2: "value"})
```
note: the collection doesn't have to already be created, this will create the document for us

insert multiple documents into a collection at once
```mongosh
db.collectionName.insertMany([{attr:"value"}, {attr:"value"}])
```


accessing documents
```mongosh
db.collectionName.find()
```
this returns the first 20 documents it encounters, then we can use `it` to iterate through the next 20 documents (this is different from the behaivior inside code)

accessing documents while filtering
```mongosh
db.collectionName.find({attr:"val", attr: "val"})
```

retrieving specific fields from a document
```mongosh
db.collectionName.find({},{fieldName: 1, fieldName: 1})
```

retrieve a single collection
```mongosh
db.collectionName.findOne({_id: ObjectId("4as6s5f46a513a2sf1d65
4s")})
```

method chaining
```mongosh
.count()
.limit(5)
.sort({ title: 1}) //alphabetically in ascending order (-1 => decending order)
```

----

### operators
[[Operators]]

----

### filter based on array-type attribute/field

*find documents where the arrAttr's value is "value"*
```mongosh
db.collectionName.find({arrAttr: "value"})
```

*find documents where the arrAttr's value has **ONLY** the following values*
```mongosh
db.collectionName.find({arrAttr: ["value", "value"]})
```

*find documents where the arrAttr's value has **(but not limited to)** the following values*
```mongosh
db.collectionName.find({arrAttr:{$all: ["val1", "val2"]}})
```

----

### filter based on nested documents

```mongosh
db.collectionName.find({"parentProperty.childProperty": "value"})
```


----

### deleting documents

```mongosh
db.collectionName.deleteOne({_id: ObjectId("65s4f654s54f5a23s1f65sf7489s")})
```

```mongosh
db.collectionName.deleteMany({filter})
```


---

### updating documents

*update a specific document*
```mongosh
db.collectionName.updateOne({_id: ObjectId("981984f65a423f1af")}, {$set: {attr: "newVal", attr2: "newVal"}})
```

```mongosh
db.collectionName.updateOne({documentFilter}, )
```

*updatee multiple documents*
```mongosh
db.collectionName.updateMany({docuementFilter}, {$set: {attr: "newVal"}})
```


