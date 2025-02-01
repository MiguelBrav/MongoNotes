# MongoDB

## Indexes 

### Single Field Index 
### Índice de campo único

#### Creates an index on a single field to improve query performance on that field.

#### Crea un índice en un solo campo para mejorar el rendimiento de consultas en ese campo.

```mongodb
db.products.createIndex({ name: 1 });

db.products.createIndex({ price: 1 });

db.products.createIndex({ internalId: 1 }, { unique: true });
```

### Multikey Index 
### Índice multikey
#### Automatically created when indexing array fields. Indexes each element of the array.
#### Se crea automáticamente al indexar campos de tipo array. Indexa cada elemento del arreglo.

_Example with array_

```mongodb
db.products.createIndex({ colors: 1 }); 
```


###  Compound Index 
### Índice compuesto
#### Creates a single index on multiple fields. The order of fields matters for query optimization.
#### Crea un único índice en múltiples campos. El orden de los campos es importante para la optimización de consultas.

```mongodb
db.products.createIndex({ name: 1, price: -1 });
```

### Get Indexes
### Obtener Índices 
#### Lists all indexes in a collection. Useful for understanding existing indexes.
#### Lista todos los índices en una colección. Útil para conocer los índices existentes.

```mongodb
db.products.getIndexes();
```

### Drop Indexes
### Eliminar Índices 
#### Removes a specific index from a collection using its name.
#### Elimina un índice específico de una colección usando su nombre.

```mongodb
db.products.dropIndex("name_1_price_-1");
```

#### Removes all indexes except the default `_id` index.
#### Elimina todos los índices excepto el índice predeterminado `_id`.

```mongodb
db.products.dropIndexes();
```


### Hide Indexes
### Ocultar Índices
#### Hides a specific index in a collection, making it inactive without deleting it.
#### Oculta un índice específico en una colección, haciéndolo inactivo sin eliminarlo.

```mongodb
db.products.hideIndex("name_1_price_-1");
```

### Unhide Indexes
### Mostrar Índices
#### Unhides a previously hidden index, making it active again.
#### Muestra un índice previamente oculto, haciéndolo activo nuevamente.

```mongodb
db.products.unhideIndex("name_1_price_-1")
```