writeCode

Write code to:-

- create a database named `mountains`
- a collection inside that database named `himalayas`
- insert 1 document into that collection `{name: 'Dhauldhar range', height: '4000 mtrs'}`

- insert multiple document using insertMany command
- find all documents from mountains
- find a single document using name


```sh
use mountains
db.createCollection("himalayas")
db.himalayas.insertOne({ name: 'Dhauldhar range', height: '4000 mtrs' })
db.himalayas.insertMany([
  { name: 'Mount Everest', height: '8848 mtrs' },
  { name: 'K2', height: '8611 mtrs' },
  { name: 'Kangchenjunga', height: '8586 mtrs' }
])
db.himalayas.find().pretty()
db.himalayas.findOne({ name: 'Mount Everest' })
```
