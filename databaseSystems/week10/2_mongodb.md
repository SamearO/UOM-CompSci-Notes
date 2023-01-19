# MongoDB

* MongoDB is a general purpose, document based distributed database.
* It contains collections of documents which are in `JSON-style` and are stored in `BSON`.
* Does not need a schema by default but can be made to have one.

## JSON Data Representation
* Data is represented in field value pairs. `name: "Gareth"`.
* Every document in a collection contains a unique `_id` field.
* Fields are seperated by commas
* Honestly its just JSON.

## MongoDB CRUD operations
```javascript
db.collectionName.insertOne(<document>) // inserting documents into a collection

db.collectionName.find({"years": {$gt: 3}}, {staff: 1, supervisors: 1}) // Displays all staff and supervisors for projects that are over 3 years

db.collectionName.updateMany({"pyears": {$gte: 5}}, {$set: {"status.finished": 1}}) // update finished status of projects who's years are more than 5

```

## MongoDB relationships

### Embedding
* Captures relations by storing it in a single document structure.
* Embeds document structures in a field or array within a document.
* Used when related items are frequently used or fetched together.
* The embedded document is not a key document.
* Related documents have similar volatility.
* Data does not change or grow much.
* There is a one to one or one to many relationship.

```json
// One to many relationship, products wouldn't be an array for one to one.
{
    "_id": "<ObjectId1>",
    "name": "Smith",
    products: [{
        "code": "Yes"
    }]
}
```

### Referencing
* Used when embedding would result in substantial data duplication.
* Used when embedded documents would grow.
* Used in many to many relationships.
* Used when fast writes are needed.

```javascript
// One User to many products
// User Document
{
    "_id": "<ObjectId1>",
    "name" : "Smith"
}

// Product document
{
    "_id" : "<ProductId1>",
    "customer_id" : "<ObjectId1>"
}

// In the case where it is a many to many relationship
{
    "_id": "<ObjectId1>",
    "name" : "Smith",
    "products" : [1,2]
}

{
    "_id" : 1,
    "customers" : ["<ObjectId1>"]
}


```