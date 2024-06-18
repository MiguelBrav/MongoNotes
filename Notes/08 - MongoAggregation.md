# MongoDB

## Mongo Aggregation

### Prepare data

### Preparar informacion

_Example_

```mongodb
db.products.insertMany([
  {
    name: "Laptop",
    price: 13000,
    stock: 30,
    colors: ["red", "black", "blue"],
    comments: { calif: 9, autor: "User1" },
    "star-review": [
      { user: "UserA", stars: 5 },
      { user: "UserB", stars: 4 }
    ]
  },
  {
    name: "Cellphone",
    price: 6000,
    stock: 5,
    colors: ["red", "yellow"],
    comments: { calif: 2, autor: "User1" },
    "star-review": [
      { user: "UserC", stars: 3 },
      { user: "UserD", stars: 2 }
    ]
  },
  {
    name: "TV",
    price: 9000,
    stock: 10,
    colors: ["red", "black", "white"],
    comments: { calif: 7, autor: "User2" },
    "star-review": [
      { user: "UserE", stars: 4 },
      { user: "UserF", stars: 5 }
    ]
  },
  {
    name: "Microphone",
    price: 3000,
    stock: 20,
    colors: ["red", "green", "blue"],
    comments: { calif: 3, autor: "User4" },
    "star-review": [
      { user: "UserG", stars: 3 },
      { user: "UserH", stars: 4 }
    ]
  },
  {
    name: "Mouse",
    price: 250,
    stock: 200,
    colors: ["red", "pink", "blue"],
    comments: { calif: 6, autor: "User9" },
    "star-review": [
      { user: "UserI", stars: 4 },
      { user: "UserJ", stars: 5 }
    ]
  }
])
```

#### Match

##### Filters the documents to pass only the documents that match the specified condition(s) to the next pipeline stage

##### Filtra los documentos para pasar solo los documentos que coinciden con las condiciones especificadas a la siguiente etapa del proceso


```mongodb
db.products.aggregate(
  [
    {
      $match:{
    stock:200
  }
    }
  ]
)
```


```mongodb
db.products.aggregate([
  {
    $match: {
      $and: [
        { stock: 200 },
        { name: "Mouse" }
      ]
    }
  }
])

```

#### Group

##### The $group stage separates documents into groups according to a "group key"

##### Separa los documentos en grupos según una "clave de grupo"


_Example calculating current stock_

```mongodb
db.products.aggregate([
  {
    $group: {
      _id: "$name",
      currentstock: { $sum: "$stock" }
    }
  }
])

```

#### Sort

##### Sorts all input documents and returns them to the pipeline in sorted order

##### Ordena todos los documentos de entrada y los devuelve.


_Example calculating current stock and sorting_

```mongodb
db.products.aggregate([
  {
    $group: {
      _id: "$name",
      currentstock: { $sum: "$stock" }
    }
  },
  {
    $sort: { currentstock: -1 }
  }
])


```

#### Projects

##### Passes along the documents with the requested fields.

##### Pasa los documentos con los campos solicitados.


_Example_

```mongodb
db.products.aggregate([
  {
    $group: {
      _id: "$name",
      currentstock: { $sum: "$stock" }
    }
  },
  {
    $project: {
      productName: "$_id",
      totalStock: "$currentstock",
      _id: 0
    }
  }
])


```
