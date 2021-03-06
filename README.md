
# MongoDb Ultimate Cheatsheet

<div>
  <img width='80%' src='https://raw.githubusercontent.com/rit-hub/public_logo_png_img/main/mongodb/mongo.jpg' alt='Mongo' />
</div>

## Mongo vs Mongod

<div>
  <img width='80%' src='https://raw.githubusercontent.com/rit-hub/public_logo_png_img/main/mongodb/mongovsmongod.jpg' alt='Mongo' />
</div>


## MySql vs MongoDb

| SQL Terms | MongoDb Terms     |
| :-------- | :------- | 
| `Database` | `Database` | 
| `Tables` | `Collections` | 
| `Rows` | `Documents (BSON*)` | 
| `Columns` | `Fields` | 
<p>*BSON - Binary JSON</p>

## Collections & Documents

<div align="center">
  <img width='40%' src='https://raw.githubusercontent.com/rit-hub/public_logo_png_img/main/mongodb/mongoCollections.jpg' alt='Mongo' />
   <img width='50%' src='https://raw.githubusercontent.com/rit-hub/public_logo_png_img/main/mongodb/mongoDocuments.jpg' alt='Mongo' />
</div>

## Database Commands

 View all databases

```bash
 show dbs
```
Create a new or switch databases 

```bash
 use dbName
```
View current Database

```bash
  db
```
Delete Database 

```bash
db.dropDatabase()
```
Show Collections

```bash
 show collections
```
Create a collection named 'comments'

```bash
 db.createCollection('comments')
```    
Drop a collection named 'comments'

```bash
 db.comments.drop()
```    
Show all Rows in a Collection 

```bash
 db.comments.find()
```    
Show all Rows in a Collection (Prettified)

```bash
db.comments.find().pretty()
```    
Find the first row matching the object

```bash
db.comments.findOne({name: 'Ritam'})
```    
Insert One Row

```bash
db.comments.insert({
    'name': 'Ritam',
    'lang': 'JavaScript',
    'member_since': 5
 })
```  
Insert many Rows

```bash
db.comments.insertMany([{
    'name': 'Ritam',
    'lang': 'JavaScript',
    'member_since': 5
    }, 
    {'name': 'Rohan',
    'lang': 'Python',
    'member_since': 3
    },
    {'name': 'Lovish',
    'lang': 'Java',
    'member_since': 4
}])
```  
Search in a MongoDb Database

```bash
db.comments.find({lang:'Python'})
```  
Limit the number of rows in output
```bash
db.comments.find().limit(2)
```  
Count the number of rows in the output
```bash
db.comments.find().count()
```  
Update a row
```bash
db.comments.update({name: 'Shubham'},
{'name': 'Ritam',
    'lang': 'JavaScript',
    'member_since': 51
}, {upsert: true})
```  
Mongodb Increment Operator
```bash
db.comments.update({name: 'Rohan'},
{$inc:{
    member_since: 2
}})
```  
Mongodb Rename Operator
```bash
db.comments.update({name: 'Rohan'},
{$rename:{
    member_since: 'member'
}})
```  
Delete Row 
```bash
db.comments.remove({name: 'Ritam'})
```  
Less than/Greater than/ Less than or Eq/Greater than or Eq
```bash
db.comments.find({member_since: {$lt: 90}})
```  
```bash
db.comments.find({member_since: {$lte: 90}})
```  
```bash
db.comments.find({member_since: {$gt: 90}})
```  
```bash
db.comments.find({member_since: {$gte: 90}})
```  
