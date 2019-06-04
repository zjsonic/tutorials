# Database Collection Document

In MongoDB:

- Database hold collections.
- Collections hold documents.
- Documents hold data records.


## Database

```sql
db -- to display the database you are using. The operation should return test, which is the default database.
show dbs; -- To list the databases available to the user.
use <myNewdb> -- To switch database, issue this command.
```

## Collection

- `show collections`
- `db.newCollection1.insertOne({ x : 1 })`: Insert a document into a collection.
- `db.collection.createIndex(keys,options)`: Create indexes on collections.

## db.collection.insertOne()

```m
db.collection.insertOne(
   <document>,
   {
      writeConcern: <document>
   }
)
```

- document: A document to insert into the collection.
- writeConcern:

## db.collection.createIndex(keys,options)

```m
db.myNewCollection3.createIndex( { y: 1 } )
```

## Document

### Document structure

```sql
{
   field1: value1,
   field2: value2,
   field3: value3,
   ...
   fieldN: valueN
}
```

- {}: wrapped in a pair of curly braces.
- field: Field names are strings.
  - `_id`: This fild name is reserved for use as a primary key.Its value must be unique in the collection, is immtable and may be any type other than an array.
  - filed name cannot contain `null` character.
  - top level filed names `cannot` start with the dollar sign character.
- value: The value of a field can be any of the BSON data types, including other documents, arrays, and arrays of documents

### Dot Notation

- Arrays: MongoDB uses the dot notation to access the elements of an array and to access the fields of an embedded document. `<array>.<index>` 
- Embedded Documents: To specify or access a field of an embedded document with dot notation, concatenate the embedded document name with the dot (.) and the field name, and enclose in quotes: `<embedded document>.<field>`

### Document Limitations

- Document Size Limit: The maximum BSON document size is 16 megabytes.
- Document Field Order: MongoDB preserves the order of the document fields following write operations except for the following cases:
  - The _id field is always the first field in the document.
  - Updates that include renaming of field names may result in the reordering of fields in the document.
- The _id Field: In MongoDB, each document stored in a collection requires a unique _id field that acts as a primary key. If an inserted document omits the _id field, the MongoDB driver automatically generates an ObjectId for the _id field

### Other Uses of the Document Structure¶

- Query Filter Documents
- Update Specification Documents


