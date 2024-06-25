writeCode

Write code to execute below expressions.

1. Create a database named `blog`.
2. Create a collection called 'articles'.
3. Insert multiple documents(at least 3) into articles. It should have fields

- title as string
- createdAt as date
- details as String
- author as nested object
  - author should have
    - name
    - email
    - age
    - example author: {name: 'abc', email: 'abc@gmail', age: 25}
- tags : Array of strings like ['html', 'css']

```js
// An article should look like in the database
{
  _id: 'some_random_id',
  title: '',
  details: '',
  author: {
    name: '',
    email: '',
    age: ''
  },
  tags: ['js', 'mongo']
}
```

4. Find all the articles using `db.COLLECTION_NAME.find()`
5. Find a document using \_id field.
6. 1. Find documents using title
7. 2. Find documents using author's name field.
8. Find document using a specific tag.

9. Update title of a document using its \_id field.
10. Update a author's name using article's title.
11. rename details field to description from all articles in articles collection.
12. Add additional tag in a specific document.

13. Update an article's title using $set and without $set.

- Write the differences here ?

13. find an article using title and increment it's auhtor's age by 5.

14. Delete a document using \_id field with `db.COLLECTION_NAME.remove()`.

// Sample data

```js
db.users.insertMany([
  {
    age: 49,
    name: "Maurice Brock",
    email: "wuk@hibpiz.ch",
    gender: "Female",
    sports: ["cricket", "football"],
    scores: [24, 35, 18, 16],
    weight: 45,
  },
  {
    age: 37,
    birthday: "7/15/1986",
    name: "Virgie Cunningham",
    email: "ezogafa@de.gm",
    gender: "Male",
    sports: ["football"],
    scores: [17, 35, 43],
    weight: 52,
  },
  {
    age: 48,
    birthday: "5/14/1961",
    name: "Alexander Holt",
    email: "han@mu.pe",
    gender: "Male",
    sports: ["cricket", "football", "TT"],
    scores: [24, 30, 16],
    weight: 55,
  },
  {
    age: 53,
    birthday: "11/15/1963",
    name: "Derek Dawson",
    email: "polril@now.de",
    gender: "Male",
    sports: ["cricket", "hockey"],
    scores: [20, 15, 38, 23],
    weight: 49,
  },
  {
    age: 34,
    birthday: "7/24/1964",
    name: "Cynthia Cobb",
    email: "wujjarpob@jecimpar.gu",
    gender: "Female",
    sports: ["cricket"],
    scores: [41, 17, 28],
    weight: 51,
  },
  {
    age: 33,
    birthday: "10/26/1982",
    name: "Isabella Atkins",
    email: "ononuzas@givhoz.ca",
    gender: "Female",
    sports: ["cricket", "football", "hockey", "TT"],
    scores: [14, 38, 29, 45, 20],
    weight: 49,
  },
  {
    age: 47,
    birthday: "10/12/1978",
    name: "Katharine Bryan",
    email: "zo@pebi.sa",
    gender: "Male",
    sports: ["TT", "hockey", "khokho"],
    scores: [27, 20, 34],
    weight: 58,
  },
  {
    age: 41,
    birthday: "1/28/1991",
    name: "Beatrice Fleming",
    email: "ufufsa@pujizren.tk",
    gender: "Female",
    sports: ["football", "khokho"],
    scores: [30, 20, 15, 29, 43],
    weight: 47,
  },
  {
    age: 26,
    birthday: "3/23/1998",
    name: "Tom Fields",
    email: "wasodjow@ofaba.gf",
    gender: "Female",
    sports: ["khokho"],
    scores: [37, 29, 18, 43, 49],
    weight: 50,
  },
  {
    age: 33,
    birthday: "11/14/1960",
    name: "Steve Ortega",
    email: "dupus@ca.ls",
    gender: "Female",
    sports: ["cricket", "football", "hockey"],
    scores: [12, 15, 20],
    weight: 51,
  },
  {
    age: 24,
    birthday: "1/5/1994",
    name: "Suraj Kumar",
    weight: 50,
    gender: "Male",
    sports: ["football", "cricket", "TT"],
  },
]);
```

Insert above data into database to perform below queries:-

- Find all males who play cricket.
- Update user with extra golf field in sports array whose name is "Steve Ortega".
- Find all users who play either 'football' or 'cricket'.
- Find all users whose name includes 'ri' in their name.




```
use blog
db.createCollection('articles')
db.articles.insertMany([
  {
    title: "Introduction to HTML",
    createdAt: new Date(),
    details: "This is an introduction to HTML.",
    author: {
      name: "John Doe",
      email: "john@example.com",
      age: 30
    },
    tags: ["html", "web development"]
  },
  {
    title: "Getting started with CSS",
    createdAt: new Date(),
    details: "This is an introduction to CSS.",
    author: {
      name: "Jane Smith",
      email: "jane@example.com",
      age: 25
    },
    tags: ["css", "design"]
  },
  {
    title: "JavaScript Basics",
    createdAt: new Date(),
    details: "This is an introduction to JavaScript.",
    author: {
      name: "Mike Johnson",
      email: "mike@example.com",
      age: 35
    },
    tags: ["javascript", "programming"]
  }
])
db.articles.find().pretty()
db.articles.findOne({ _id: ObjectId("667a7411aac6961bb5cc8989") })
db.articles.find({ title: "JavaScript Basics" }).pretty()
db.articles.find({ "author.name": "Jane Smith" }).pretty()
db.articles.find({ tags: "css" }).pretty()
db.articles.updateOne(
  { _id: ObjectId("667a7411aac6961bb5cc8989") },
  { $set: { title: "Advanced JavaScript" } }
)
db.articles.updateOne(
  { title: "Introduction to HTML" },
  { $set: { "author.name": "Johnny Doe" } }
)
db.articles.updateMany(
  {},
  { $rename: { "details": "description" } }
)
db.articles.updateOne(
  { title: "Getting started with CSS" },
  { $push: { tags: "responsive design" } }
)
db.articles.updateOne(
  { title: "JavaScript Basics" },
  { $set: { title: "JavaScript for Beginners" } }
)
db.articles.updateOne(
  { title: "JavaScript for Beginners" },
  { title: "JavaScript Basics Again" }
)
db.articles.updateOne(
  { title: "Advanced JavaScript" },
  { $inc: { "author.age": 5 } }
)
db.articles.remove({ _id: ObjectId("667a7411aac6961bb5cc8989") })

//after inserting the user sample data

db.users.find({ gender: "Male", sports: "cricket" }).pretty()
db.users.updateOne(
  { name: "Steve Ortega" },
  { $push: { sports: "golf" } }
)
db.users.find({ sports: { $in: ["football", "cricket"] } }).pretty()
db.users.find({ name: /ri/ }).pretty()




```
