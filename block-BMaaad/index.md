writeCode

Write command to

- List collections from a database.
- create a new collection in your country database which you created recently.
```
showColection
db.createCollection('Himachal_Pradesh')
```

Write code to:-

- crate a database named `weather`
- create a capped collection named `temperature` with maximum of 3 documents and try inserting more than 3 to see the result.
- create a simple collection named `humidity`
- check whether `temperature` collection is capped or not ?
- Delete `humidity` collection and then the entire database(weather).

```
//crate a database named `weather`
use weather
// create a capped collection named `temperature` with maximum of 3 documents and try inserting more than 3 to see the result.
db.createCollection("temperature", { capped: true, size: 5000, max: 3 })
db.temperature.insertMany([
  { temp: 20, date: new Date() },
  { temp: 22, date: new Date() },
  { temp: 24, date: new Date() },
  { temp: 26, date: new Date() }
])
// create a simple collection named `humidity`
db.createColection('humidity')
// check whether `temperature` collection is capped or not ?
//- Delete `humidity` collection and then the entire database(weather).
db.humidity.drop()
db.dropdatabase()
```