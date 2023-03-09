# Java using MongoDB

- A MongoDB hosts a number of databases
- A database is a physical data container of a set of collections
- A collection contains a set of documents
- A document contains a set of key-value (aka field_name/field_value) pairs
  {field1: value1,..., fieldn: valuen}

Document

```
{
  name: 'John',
  age: 25,
  status: 'A',
  groups: ['news','sports']
}
```

Mongodb shell
MongoDB adds the field \_id automatically

```shell
# Insert Document(Json/Bson)
# Bson working on the Document object
db.users.insert({
  name: 'John',
  age: 25,
  status: 'A',
  groups: ['news','sports']
})

# db.users.find()

# db.users.aggregation()

db.courses.update (
  {code:“SWEN432”},
  {set:{year:2015}}
)
db.courses.remove (
	{year:{$lt:2014}}
)

# map -> reduce
db.users.find({age:{${gt: 18}}}).sort({age:1})

# A list of fields to return (designated by {<field_name>: 1}), or
# A list of fields to exclude (designated by {<field_name>: 0}) in the result,
# Only the exclusion of _id field can be mixed with fields to return
db.courses.find({no_of_st:{$gt:8}}{title:1,_id:0})
db.courses.find({no_of_st:{ $gt:8}}{title:0})

# Aggregating of sum (Pipeline)
# total is the new nameing of the results
db.orders.aggregate([
  {$match:{status:"A"}},
  {$group:{_id:"cust_id",total:{$sum:"$amount"}}}
])


```

```
db.orders.insertMany([
   { _id: 1, cust_id: "Ant O. Knee", ord_date: new Date("2020-03-01"), price: 25, items: [ { sku: "oranges", qty: 5, price: 2.5 }, { sku: "apples", qty: 5, price: 2.5 } ], status: "A" },
   { _id: 2, cust_id: "Ant O. Knee", ord_date: new Date("2020-03-08"), price: 70, items: [ { sku: "oranges", qty: 8, price: 2.5 }, { sku: "chocolates", qty: 5, price: 10 } ], status: "A" },
   { _id: 3, cust_id: "Busby Bee", ord_date: new Date("2020-03-08"), price: 50, items: [ { sku: "oranges", qty: 10, price: 2.5 }, { sku: "pears", qty: 10, price: 2.5 } ], status: "A" },
   { _id: 4, cust_id: "Busby Bee", ord_date: new Date("2020-03-18"), price: 25, items: [ { sku: "oranges", qty: 10, price: 2.5 } ], status: "A" },
   { _id: 5, cust_id: "Busby Bee", ord_date: new Date("2020-03-19"), price: 50, items: [ { sku: "chocolates", qty: 5, price: 10 } ], status: "A"},
   { _id: 6, cust_id: "Cam Elot", ord_date: new Date("2020-03-19"), price: 35, items: [ { sku: "carrots", qty: 10, price: 1.0 }, { sku: "apples", qty: 10, price: 2.5 } ], status: "A" },
   { _id: 7, cust_id: "Cam Elot", ord_date: new Date("2020-03-20"), price: 25, items: [ { sku: "oranges", qty: 10, price: 2.5 } ], status: "A" },
   { _id: 8, cust_id: "Don Quis", ord_date: new Date("2020-03-20"), price: 75, items: [ { sku: "chocolates", qty: 5, price: 10 }, { sku: "apples", qty: 10, price: 2.5 } ], status: "A" },
   { _id: 9, cust_id: "Don Quis", ord_date: new Date("2020-03-20"), price: 55, items: [ { sku: "carrots", qty: 5, price: 1.0 }, { sku: "apples", qty: 10, price: 2.5 }, { sku: "oranges", qty: 10, price: 2.5 } ], status: "A" },
   { _id: 10, cust_id: "Don Quis", ord_date: new Date("2020-03-23"), price: 25, items: [ { sku: "oranges", qty: 10, price: 2.5 } ], status: "A" }
])

db.orders.aggregate([{$match: {status: "A"}}, $group: {_id: "$cust_id", cout:${sum: 1}}])

# flattening -> help group the item
```

### ETL

dataset ->
