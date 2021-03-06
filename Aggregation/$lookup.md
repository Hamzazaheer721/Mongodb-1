
You can also use the pipeline stage to perform checks on a sub-docunment array

Here's the example using python (sorry I'm snake people).

db.products.aggregate([
  { '$lookup': {
      'from': 'products',
      'let': { 'pid': '$products' },
      'pipeline': [
        { '$match': { '$expr': { '$in': ['$_id', '$$pid'] } } }
        // Add additional stages here 
      ],
      'as':'productObjects'
  }
])
The catch here is to match all objects in the ObjectId array (foreign _id that is in local field/prop products).

You can also clean up or project the foreign records with additional stages, as indicated by the comment above.


============== EXAMPLE 2 ===================

EpikBoxes is an array of object. We can use it like that as well.

db.orders.aggregate([
  {
    "$lookup": {
      "from": "epikBox",
      "localField": "assignedTo",
      "foreignField": "assignedTo",
      "as": "EpikBoxes"
    }
  },
  {
    "$lookup": {
      "from": "user",
      "localField": "EpikBoxes._id",
      "foreignField": "_id",
      "as": "users"
    }
  }
])


