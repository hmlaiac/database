# Commands
## 1. MongoDB Indexing
```
db.stores.insertMany( 
   [ 
     { _id: 1, name: "Java Hut", description: "Coffee and cakes" }, 
     { _id: 2, name: "Burger Buns", description: "Gourmet hamburgers" }, 
     { _id: 3, name: "Coffee Shop", description: "Just coffee" }, 
     { _id: 4, name: "Clothes Clothes Clothes", description: "Discount clothing" }, 
     { _id: 5, name: "Java Shopping", description: "Indonesian goods" } 
   ] 
) 
db.stores.createIndex( { name: "text", description: "text" } ) //both in text
db.stores.find({ $text: {$search: "Coffee" } }) 
db.stores.find({ $text: {$search: "Java Hut Coffee" } }) 
db.stores.find( 
   { $text: { $search: "java hut coffee" } }, 
   { score: { $meta: "textScore" } } 
).sort( { score: { $meta: "textScore" } } )
```

## 2. Aggregation
```
db.purchase_orders.insertMany( 
     [ 
          {product: "toothbrush", total: 4.75, customer: "Mike"}, 
          {product: "guitar", total: 199.99, customer: "Tom"}, 
          {product: "milk", total: 11.33, customer: "Mike"}, 
          {product: "pizza", total: 8.50, customer: "Karen"}, 
          {product: "toothbrush", total: 4.75, customer: "Karen"}, 
          {product: "pizza", total: 4.75, customer: "Dave"} 
          {product: "toothbrush", total: 4.75, customer: "Mike"}, 
     ] 
) 
// find out how many toothbrushes were sold 
db.purchase_orders.count({product: "toothbrush"}) 
// Find list of all products sold 
db.purchase_orders.distinct("product") 
// Find the total amount of money spent by each customer 
db.purchase_orders.aggregate( 
     [ 
          {$match: {} }, 
          {$group: {_id: "$customer", total: { $sum: "$total"} } } 
     ] 
) 
// Find how much has been spent on each product and sort it by price 
db.purchase_orders.aggregate( 
     [ 
          {$match: {} }, 
          {$group: {_id: "$product", total: { $sum: "$total"} } }, 
          {$sort: {total: -1}} 
     ] 
) 
// Find how much money each customer has spent on toothbrushes and pizza 
db.purchase_orders.aggregate( 
     [ 
          {$match: {product: {$in: ["toothbrush", "pizza"]} } }, 
          {$group: {_id: "$product", total: { $sum: "$total"} } }, 
     ] 
) 
// https://docs.mongodb.com/manual/reference/operator/aggregation/ 
// Show the list of all pipeline operators
```

## 3. MongoDB bulkWrite
```
db.students.bulkWrite( 
      [ 
         { insertOne : 
            { 
               "document" : 
               { 
                  name: "Andrew", major: "Architecture", gpa: 3.2 
               } 
            } 
         }, 
         { insertOne : 
            { 
               "document" : 
               { 
                  name: "Terry", major: "Math", gpa: 3.8 
               } 
            } 
         }, 
         { updateOne : 
            { 
               filter : { name : "Terry" }, 
               update : { $set : { gpa : 4.0 } } 
            } 
         }, 
         { deleteOne : 
            { filter : { name : "Kate"} } 
         }, 
         { replaceOne : 
            { 
               filter : { name : "Claire" }, 
               replacement : { name: "Genny", major: "Counsling", gpa: 2.4 } 
            } 
         } 
    ], 
    {ordered: false} 
   );
```