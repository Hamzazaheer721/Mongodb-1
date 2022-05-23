// If you want to add a new_field to all your collection, you have to use empty
// selector, and set multi flag to true (last param) to update all the documents

db.your_collection.update(
  {},
  { $set: {"new_field": 1} },
  false,
  true
)

// In the above example last 2 fields false, true specifies the upsert and multi flags.
// Upsert: If set to true, creates a new document when no document matches the query criteria.
