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
  
- $unset (Removing a field in migration)
  - for example:
      { "_id" : 1, "name" : "Wag", "type" : "Dog", "weight" : 20 }
      { "_id" : 2, "name" : "Bark", "type" : "Dog", "weight" : 10 }
      { "_id" : 6, "name" : "Fetch", "type" : "Dog", "weight" : 17 }
      { "_id" : 7, "name" : "Jake", "type" : "Dog", "weight" : 30 }
  - db.dogs.updateMany({}, { $unset: { type: "" }});
  - Output: { "acknowledged" : true, "matchedCount" : 4, "modifiedCount" : 4 }
  
  - Using db.dogs.find()
    { "_id" : 1, "name" : "Wag", "weight" : 20 }
    { "_id" : 2, "name" : "Bark", "weight" : 10 }
    { "_id" : 6, "name" : "Fetch", "weight" : 17 }
    { "_id" : 7, "name" : "Jake", "weight" : 30 
  - For Removing multiple fields => db.dogs.updateMany({}, { $unset: { name: "", weight: ""} } );

  - For Embedded Documents 
      {
        "_id" : 1,
        "name" : "Wag",
        "details" : {
          "type" : "Dog",
          "weight" : 20,
          "awards" : {
            "Florida Dog Awards" : "Top Dog",
            "New York Marathon" : "Fastest Dog",
            "Sumo 2020" : "Biggest Dog"
          }
        }
      }
  - To remove "awards" => db.pets.updateMany( { _id: 1 }, { $unset: { "details.awards": "" } } )
  - Output: { "acknowledged" : true, "matchedCount" : 1, "modifiedCount" : 1 }
  - Result:
     {
        "_id" : 1,
        "name" : "Wag",
        "details" : {
          "type" : "Dog",
          "weight" : 20
        }
      }
