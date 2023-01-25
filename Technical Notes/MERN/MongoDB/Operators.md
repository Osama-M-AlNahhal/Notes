#mongodb_operators 

----

[documentation](https://www.mongodb.com/docs/manual/reference/operator/query/)

----
# Operators list
## or
```bson
{$or: {filter1}, {filter2}}
```

## and 
```bson
{$and: {filter1}, {filter2}}
```

## in
```bson
{$in: ["val1", "val2", "val3"]}
```

## nin
```bson
{$nin: ["val1", "val2", "val3"]}
```

## all
```bson
{$all: ["val1", "val2", "val3"]}
```

## inc & dec
```bson
{$inc: {fieldToIncrement: incrementBy}}
```
*decrementing => negative value*

## push & pull
*add or remove specific values from array-type fields*
```bson
{$push: {arrAttr: "val"}}
```

```bson
{$pull: {arrAttr: "val"}}
```

