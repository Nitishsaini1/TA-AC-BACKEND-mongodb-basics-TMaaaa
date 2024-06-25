writeCode

Write code to:-

- create a database named `sports`.
```
use sports
```
- list all databases present in local mongod server.
```
show dbs
```
- create 3 collections named `cricket`, `football`, `TT` in sports databse.
```
db.createCollection("cricket")
db.createCollection("football")
db.createCollection("TT")
```
- add multiple players in those collections which should have fields like `name`, `age` and `email` and `bid_price`.
```

db.cricket.insertMany([
  { name: "Virat Kohli", age: 32, email: "virat@example.com", bid_price: 2000000 },
  { name: "MS Dhoni", age: 39, email: "dhoni@example.com", bid_price: 1800000 }
])
db.football.insertMany([
  { name: "Messi", age: 32, email: "messi@example.com", bid_price: 1200000 },
  { name: "Christiano Ronaldo", age: 39, email: "christiano@example.com", bid_price: 2330000 }
])
db.TT.insertMany([
  { name: "First", age: 32, email: "first@example.com", bid_price: 5000000 },
  { name: "Second", age: 39, email: "second@example.com", bid_price: 600000 }
])
```
- list all collections in sports database.
```
show collection
```
- rename `TT` collection to `tennis`.
```
db.TT.renameCollection('Tennis')
```
- create a capped collection called `khokho` which should have max 3 documents.
```
db.createCollection('khokho',{
  capped:true,
  size:12345,
  max:3
})
```
- Try inserting more than 3 and see what happens?
```
db.khokho.insertMany([
  {name :Player1, age:23, email:player1@email.com, bid_price:230000},
  {name :Player2, age:23, email:player2@email.com, bid_price:430000},
  {name :Player3, age:23, email:player3@email.com, bid_price:530000}
])
//try inserting fourth one
db.khokho.insertMany([
  {name :Player4, age:23, email:player4@email.com, bid_price:230000}
])
```
- check whether a collection is capped or not?
```
db.khokho.isCapped()
```
- drop all documents from `football` collection.
```
db.football.deleteMany({})
```
- delete cricket collection completely.
```
db.cricket.drop()
```
- delete sports database.
```
use sports
db.dropDatabase()
```
- check which database you are connected to ?
```
db
```
- connect to test database
```
use test
```