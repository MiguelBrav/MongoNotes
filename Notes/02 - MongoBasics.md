# MongoDB

## Basic Crud Operations

### Create a collector for practice

### Creamos una coleccion para practica

```mongodb
use teachers
```

**Insert document to collection**

**Insertar un documento a una coleccion**

```mongodb
db.collectionName.insertOne({
    propertyName: value
})
```

_Example_

```mongodb
db.teachers.insertOne({
name: "Miguel Segura",
email: "miguelteacher@gmail.com",
phone: 7821110099})
```

**Search all documents in collection**

**Buscar todos los documentos en una coleccion**

```mongodb
db.collectionName.find()
```

_Example_

```mongodb
db.teachers.find()
```

**Update one document by id**

**Actualizar un documento por Id**

```mongodb
db.collectionName.updateOne({
    "_id": ObjectId("idObject")},
    {$set: {valueToUpdate: newValue}
})
```

_Example_

```mongodb
db.teachers.updateOne({
    "_id": ObjectId("65dd05b3a61b4730e52c5b78")},
    {$set: {name: "Miguel Segura Bravo"}
})
```

**Delete one document by id**

**Eliminar un documento por Id**

```mongodb
db.collectionName.deleteOne({
    "_id": ObjectId("idObject")
})
```

_Example_

```mongodb
db.teachers.deleteOne({
    "_id": ObjectId("65dd05b3a61b4730e52c5b78")
})
```

## Insert Many

### Create a collector for practice

### Creamos una coleccion para practica

```mongodb
use colors
```

**Insert documents to a collection**

**Insertar documentos a una coleccion**

```mongodb
db.collectionName.insertMany([{
    propertyName: value
},{
    propertyName: value
},{
    propertyName: value
}])
```

_Example_

```mongodb
db.colors.insertMany([{
name: "red",rgb:"#FA2119"},{
name: "blue",rgb:"#2AFAE3"},{
name: "black",rgb:"#000000"}])
```

_Example with Id_

```mongodb
// Coment in mongodb shell
db.colors.insertMany([{
_id:1,name: "red",rgb:"#FA2119"},{
_id:2,name: "blue",rgb:"#2AFAE3"},{
_id:3,name: "black",rgb:"#000000"}])
```

## Find operations

### Create a collector for practice

### Creamos una coleccion para practica

```mongodb
use cats
```

**Insert data for practice**
**Insert data for practice**

```mongodb
db.cats.insertMany([
{name: "Mishu",age:1,catBreed:"Siames"},
{name: "Blu",age:3,catBreed:"Bombay"},
{name: "Ramiro",age:7,catBreed:"Siberian"},
{name: "Felgrand",age:4,catBreed:"Persian"},
{name: "Anubis",age:10,catBreed:"Bengal"},
{name: "Gunger",age:12,catBreed:"Russian Blue"},
{name: "Mixiote",age:4,catBreed:"Domestic Shorthair"},
{name: "nibbler",age:2,catBreed:"European Shorthair"}
])

```

**Search documents by filter (gte - greater than or equal)**

**Buscar documentos por filtro (gte - mayor o igual)**

```mongodb
db.cats.find({ age: { $gt: 3 } })
```

**Search documents by filter (gte - greater than or equal & lte - low than or equal)**

**Buscar documentos por filtro (gte - mayor o igual y lte - menor o igual)**

```mongodb
db.cats.find({ age: { $gte: 2, $lte: 10 } })
```

**Search documents by filter (property name)**

**Buscar documentos por filtro (nombre de propiedad)**

```mongodb
db.cats.find({ name: "Gunger" })
```

**Search documents by filter (id)**

**Buscar documentos por filtro (id)**

```mongodb
db.cats.find({ "_id": ObjectId("65dd5fed5c559b38e0cd4a30") })
```

## Find operations with advanced functions

**ForEach example with property name**
**ForEach ejemplo con nombre de propiedad**

```mongodb
db.cats.find({}).forEach(function(cat) {
print(cat.name);
})
```

**Limit total results**
**Limitar el total de resultados**

```mongodb
db.cats.find({}).limit(3)
```

**Skip results**
**Saltar resultados**

```mongodb
db.cats.find({}).skip(1).limit(3)
```

**Order by property**
**Ordenar por propiedad**

_Example order descending_
```mongodb
db.cats.find({}).sort({age:-1})
```
_Example order ascending_
```mongodb
db.cats.find({}).sort({age:1})
```
## Update operations

**Update documents by filter**

**Actualizar documentos por filtro**

_Example with Update - Deprecated_
```mongodb
db.cats.update({
    "age":4},
    {$set: {"age":7}},
    {multi:true})
```

_Example with UpdateMany_
```mongodb
db.cats.updateMany(
    { "age": 7 },
    { $set: { "age": 4 } }
)
```

## Replace operations

**Replace a document** 

**Reemplazar un documento** 

_Example by Id_
```mongodb
db.cats.replaceOne(
    { "_id": ObjectId("65dd5fed5c559b38e0cd4a32") },
    { name:"nibbler 2",age:3,catBreed:"European hair"}
)
```

_Example by property name_
```mongodb
db.cats.replaceOne(
    { "name": "nibbler 2" },
    { name:"nibbler",age:3,catBreed:"European hair"}
)
```

## Mongo Proyections

**Proyections**
**Proyecciones**

```mongodb
db.cats.find({}, { _id: 0 })
```

```mongodb
db.cats.find({}, { _id: 0, age:1 })
```

```mongodb
db.cats.find({}, { _id: 0,age:1,catBreed:2})
```