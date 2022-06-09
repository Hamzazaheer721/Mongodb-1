- we can access the object attributes inside array using elemMatch
- db.orders.find({
    "modems": {
      $elemMatch: {
        "type": {
          $eq: "online"
        }
      }
    }
  },
  {
    "modems.$": 1,
    "quantity": 1
  })
- "modems.$" will return only that object in the array where the condition was satisfied.



/// SAMPLE DB ///

- orders": [
    {
      "_id": 1,
      "item": "almonds",
      "price": 12,
      "quantity": 2,
      "modems": [
        {
          type: "online"
        }
      ]
    },
    {
      "_id": 2,
      "item": "pecans",
      "price": 20,
      "quantity": 1,
      "modems": [
        {
          type: "offline"
        }
      ]
    },
    {
      "_id": 3
    },
    {
      "_id": 4,
      "item": "pecans2",
      "price": 202,
      "quantity": 12,
      "modems": [
        {
          type: "offline"
        },
        {
          type: "online"
        }
      ]
    },
    
  ],
