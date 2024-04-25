# MongoDB

## Mongo Operators

### Prepare data

### Preparar informacion

_Example_

```mongodb
db.products.insertMany([{
name: "Laptop",price:13000,stock: 30},
{name: "Cellphone",price:6000,stock: 5},
{name: "TV",price:9000,stock: 10},
{name: "Microphone",price:3000,stock: 20},
{name: "Mouse",price:250,stock: 200}
])
```
### search

###  busqueda

#### Comparation

#### Comparacion

```mongodb
Equal
db.products.find({price:{$eq:3000}})
Greater than
db.products.find({price:{$gt:3000}})
Lower than
db.products.find({price:{$lt:3000}})
Greater or equal than
db.products.find({price:{$gte:3000}})
Lower or equal than
db.products.find({price:{$lte:3000}})
```

#### Logics

#### Logicos

_And_
```mongodb
db.products.find({
    $and: [
        { price: { $gte: 3000 } },
        { stock: { $gt: 5 } }
    ]
})
```

_Or_
```mongodb
db.products.find({
    $or: [
        { price: { $gte: 3000 } },
        { stock: { $gt: 5 } }
    ]
})
```

_Or with negation_
```mongodb
db.products.find({
    $or: [
        { price: { $not: { $gte: 3000 } } },
        { stock: { $gt: 5 } }
    ]
})
```

