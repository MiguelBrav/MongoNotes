# MongoDB

## Collection backup

### Back up a collection

### Respaldar una colección

_Example with all collections_
```mongodb
mongodump
```

_Example with collection cats_
```mongodb
mongodump --db cats --out .
```

### Restore a colecction

### Restaurar una colección

_Example with collection cats (Deprecated)_
_name collection and folder "cats"_

```mongodb
mongorestore --db cats_cop cats
```

_Example with collection cats (Deprecated)_
```mongodb
mongorestore --nsInclude=cats.cats dump/
```

### Drop a collection

### Borrar una colección
```mongodb
use cats_cop

db.cats.drop()
```

### Drop database

### Borrar base de datos
```mongodb
db.dropDatabase()
```