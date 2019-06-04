# CRUD

- C: create 增
- R: retrieve 检
- U: update 改
- D: delete 删

## Insert Documents

```sql
db.collection.insert() --Insert a single document or multiple documents into a collection.
db.collection.insertOne( document ) -- Insert a single document into a collection.
db.collection.insertMany([array documents]) --Insert many documents into a collection. 
```

## Retrieve Documents

- Select All Documents in a Collection¶
- Specify Equality Condition¶
- Specify Conditions Using Query Operators
- Specify AND Conditions¶
- Specify OR Conditions¶
- Additional Query Tutorials¶
- Additional Methods

```sql
db.inventory.find() -- returns an array
db.inventory.find( {} ) -- corresponds to SELECT * FROM inventory
db.inventory.find( { item: "canvas" } )
db.inventory.find( { status: "D" } ) -- corresponds to SELECT * FROM inventory WHERE status = "D"
db.inventory.find( { status: { $in: [ "A", "D" ] } } ) -- use the $in operator rather than the $or operator. corresponds to SELECT * FROM inventory WHERE status in ("A", "D")
db.inventory.find( { status: "A", qty: { $lt: 30 } } ) --SELECT * FROM inventory WHERE status = "A" AND qty < 30
db.inventory.find( { $or: [ { status: "A" }, { qty: { $lt: 30 } } ] } ) --SELECT * FROM inventory WHERE status = "A" OR qty < 30
db.inventory.find( {
     status: "A",
     $or: [ { qty: { $lt: 30 } }, { item: /^p/ } ]
} ) --SELECT * FROM inventory WHERE status = "A" AND ( qty < 30 OR item LIKE "p%")

db.inventory.find().count() -- count the length of the result




```

## Update Documents

### db.collection.update(`<filter>, <update>, <options>`)

**Updates or Replacs one document that match a specified filter** or **updates all documents that match a specified filter**

  - db.inventory.update({name:'zhang san'}, { age: 29 })
  - db.inventory.update({ name: 'zhangsan' }, { $set: { age:29 } }): 
  - db.inventory.update({ name: 'zhangsan' }, { $set: { age:29 } }) :默认只修改一条记录
- db.collection.updateOne(`<filter>, <update>, <options>`)
  - db.inventory.updateOne()
- db.collection.updateMany(`<filter>, <update>, <options>`)
- db.collection.replaceOne(`<filter>, <update>, <options>`)

Update Operators

- `$set`: Sets the value of a field in a document.
- `$unset`: Removes the specified field from a document.


## Delete Documents