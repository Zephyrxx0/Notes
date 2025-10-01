
# Shell Commands

## Create Databases
You can change or create a new database by typing "use" then the name of the database.

Create a new database called "blog":

> [!NOTE] `use blog`
  >>[!warning] A new database is not created until it gets content
> 

## Create Collections

Two ways
- `db.createCollection("posts")`
- `db.posts.insertOne(object)` Here, if `posts` collection is not already created, it will create now

## Insert Data

- `insertOne()`
  >[!Example] Insert single element
> ```js
> db.posts.insertOne({
>   title: "Post Title 1",
>   body: "Body of post.",
>   category: "News",
>   likes: 1,
>   tags: ["news", "events"],
>   date: Date()
> })
> ```

- `insertMany()`

> [!Example] Insert multiple elements at once
> ``` js
>db.posts.insertMany([  
>   {
>     title: "Post Title 2",
>     body: "Body of post.",
>     category: "Event",
>     likes: 2,
>     tags: ["news", "events"],
>     date: Date()
>   },
>   {
>     title: "Post Title 3",
>     body: "Body of post.",
>     category: "Technology",
>     likes: 3,
>     tags: ["news", "events"],
>     date: Date()
>   },
>   {
>     title: "Post Title 4",
>     body: "Body of post.",
>     category: "Event",
>     likes: 4,
>     tags: ["news", "events"],
>     date: Date()
>   }
> ])`
> ```

## Find Data

- `find()`

> [!example] Find and return all elements in collection `post`
> `db.posts.find()`

- `findOne()`
> [!example] Find and return  elements in collection `post`
> `db.posts.findOne() // returns the first element`
> `db.posts.findOne( {category: "News"} ) // returns the first match of the query `

### Projection

Both find methods accept a second parameter called projection.
This parameter is an object that describes which fields to include in the results.

Note: This parameter is optional. If omitted, all fields will be included in the results.

Example
This example will only display the title and date fields in the results.

`db.posts.find({}, {title: 1, date: 1}) `

## Update Data

- `updateOne()`

> [!example] Update the first document that is found matching the provided query.
> `db.posts.updateOne( { title: "Post Title 1" }, { $set: { likes: 2 } } ) `


- `updateMany()`

>[!example] Update all documents that match the provided query.
>`db.posts.updateMany({}, { $inc: { likes: 1 } })`

## Delete Data


- `deleteOne()`
>[!example] delete the first document that matches the query provided
>`db.posts.deleteOne({ title: "Post Title 5" })`



- `deleteMany()`
>[!example] delete the all document that matches the query provided
>`db.posts.deleteMany({ title: "Post Title 5" })`

