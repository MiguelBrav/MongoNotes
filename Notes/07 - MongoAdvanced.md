# MongoDB

## Mongo Advanced

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

#### Exists

#### Existe

```mongodb
Exists property price
db.products.find({price:{$exists:true}})

db.products.find({price:{$exists:true,$type:"int"}})
```

#### Regex

#### Regex

```mongodb
Example
db.products.find({name:{$regex:/"YOUR REGEX"/}})

Regex by text start
db.products.find({name:{$regex:/^Lap/}})

```

#### Sort

#### Orden

```mongodb
Example
Desc
db.products.find().sort({stock:-1})

Asc
db.products.find().sort({stock:-1})

```

#### Filter array by size

#### Filtrar arreglo por tamaño

```mongodb
Example
db.products.find({colors:{$size:2}})

db.products.find({colors:{$size:3}})

```

#### Filter array by all 
##### Each one of them must be in the records.

#### Filtrar arreglo por "all"
##### Deben estar cada uno de ellos en los registros

```mongodb
Example
db.products.find({colors:{$all:["red","blue"]}})

```

#### Element match
##### Search for an item that meets the conditions

####  Buscar por coincidencia de elemento
##### Busca por un elemento que cumpla las condiciones

```mongodb
Example
db.products.find({
  "star-review": {
    $elemMatch: {
      user: "UserE",
      stars: 4
    }
  }
})

```

#### Search by object inside

####  Buscar por objeto referenciado


```mongodb
Example
db.products.find({
  "comments.calif": 6,
  "comments.autor": "User9"
})

```


#### Slice
##### Only take the elements declared in the slice (example 1) and that have the specific tag.

####  Rebanada
##### Solo toma los elementos declarados en el slice (ejemplo 1) y que tengan el tag especifico

```mongodb
Example
db.products.find({}, {
  "star-review": { $slice: 1 }
})
```
