# MongoDB

## Mongo References

### Example with Embedded Documents

### Ejemplo con documentos incrustados
    
```mongodb
db.users.insertOne({"name":"Test","email":"miguel@gmail.com","subtype":{"nametype":"basic","auth":1}})
```

```mongodb
db.users.insertOne({"name":"Test2","email":"miguel2@gmail.com","subtype":{"nametype":"basic","auth":2}})
```

### Search by Embedded Documents

### Buscar en documentos incrustados
```mongodb
db.users.find({"subtype.nametype":"basic"})
```

### Example with Reference Documents

### Ejemplo con documentos referenciados
```mongodb
db.owners.insertOne({
    "_id": 1,
    "name": "Mark Pat",
    "age": 23,
    "pets": [
        1,
        2
    ]
})

db.pets.insertMany([
    {
        "_id": 1,
        "name": "Fluffy",
        "species": "Perro",
        "ownerId": 1
    },
    {
        "_id": 2,
        "name": "Whiskers",
        "species": "Gato",
        "ownerId": 1
    }
])
```

### Search by Reference Documents

### Buscar en documentos referenciados
```mongodb
db.pets.find({"ownerId":1})
```