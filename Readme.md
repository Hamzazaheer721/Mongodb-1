- Mongosh

-- type mongosh to run the mongodb shell

- show dbs (to get all the dbs)
- use DB_NAME (to create and switch to dbs)
- show collections (shows collections inside the db)
- db.dropDatabase (drops the current database)
- exit (exit command to exit from mongosh)

- db -> collections -> documents

- Insert Methods

  - insertOne() --> lets you add an object/document into collection
  - insertMany() --> lets you add array of objects/documents into collection

- Limit

  - db.user.find().Limit(2) --> it will give the first two documents in the collection

- sort

  - db.users.find().sort( { name: 1 } ) --> It will give us the documents in alphabetical order (Capital letters come first A-Z then lower case letters will come a-z)
  - db.users.find().sort( { name: -1 } ) --> It will give us the documentts in reverse alphabetical order.

- Sort & Limit

  - db.users.find().sort( { name: 1 } ).limit(2) --> First two elements sorted in alphabetical order
  - db.users.find().sort( { name: -1 } ).limit(2) --> First two elements sorted in reverse-alphabetical order
  - db.users.find().sort( { name: 1, age: 1 } ).limit(2) --> First two elements sorted in
    - Ascending age order(elements without age attribute will start first, followed by document with lowest age)
    - Alphabetically order name attribute

- find()
  to-be-continued
