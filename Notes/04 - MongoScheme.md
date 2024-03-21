# MongoDB

## Mongo Scheme

### Define a mongo scheme

### Definir un schema en mongo

_Example create a defined scheme for mongo_
```mongodb
db.createCollection("professors", {
   validator: {
      $jsonSchema: {
         bsonType: "object",
         required: ["name", "age","subject"],
         properties: {
            name: {
               bsonType: "string",
               description: "Must be a valid name"
            },
            age: {
               bsonType: "int",
               minimum: 18,
               description: "Must be greater or equal to 18"
            },
            subject: {
               bsonType: "string",
               description: "Must be a valid subject"
            },
         }
      }
   }
})
```

_Example valid of insert with this scheme_
```mongodb
db.professors.insertOne({
name: "Miguel Segura",
age:18,
subject: "History"})
```

_Example invalid of insert with this scheme_
```mongodb
db.professors.insertOne({
name: "Miguel Segura",
age:16,
subject: true})
```