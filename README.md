# Ejercicio MongoDB 2

**1)** En `sample_training.companies`, ¿cuántas empresas tienen
más empleados que el año en el que se fundaron?

> use sample_training

```
db.companies.countDocuments({$expr:{$gt: ["$number_of_employees", "$founded_year"]}})
```

**2)** En `sample_training.companies`, ¿en cuántas empresas
coinciden su permalink con su twitter_username?

```
db.companies.countDocuments({$expr:{$eq: ["$permalink", "$twitter_username"]}})
```

**3)** En `sample_airbnb.listingsAndReviews`, ¿cuál es el nombre
del alojamiento en el que pueden estar más de 6 personas
alojadas y tiene exactamente 50 reviews?

> use sample_airbnb

```
db.listingsAndReviews.find({"accommodates":{$gt: 6}, "number_of_reviews": 50}, {name:1, _id: 0})
```

**4)** En `sample_airbnb.listingsAndReviews`, ¿cuántos documentos tienen el "property_type" "House" e incluyen "Changing table" como una de las "amenities"?

```
db.listingsAndReviews.countDocuments({property_type: "House", amenities:"Changing table"})
```

**5)** En `sample_training.companies`, ¿Cuántas empresas tienen
oficinas en Seattle?

> use sample_training

```
db.companies.countDocuments({"offices.city": "Seattle"})
```

o

```
db.companies.countDocuments({"offices": {$elemMatch: {city: "Seattle"} } })
```

**6)** En `sample_training.companies`, haga una query que devuelva únicamente el nombre de las empresas que tengan exactamente 8 "funding_rounds"

```
db.companies.countDocuments({funding_rounds: {$size: 8 }}, {name:1, _id: 0})
```

**7)** En `sample_training.trips`, ¿cuántos viajes empiezan en estaciones que están al oeste de la longitud -74?
```
db.trips.countDocuments({'start station location.coordinates.0': {$lt: -74} })
```

**8)** En `sample_training.inspections`, ¿cuántas inspecciones se llevaron a cabo en la ciudad de "NEW YORK"?
```
db.inspections.countDocuments({"address.city": "NEW YORK"})
```

**9)** En `sample_airbnb.listingsAndReviews`, haga una query que devuelva el nombre y la dirección de los alojamientos que tengan "Internet" como primer elemento de "amenities"

> use sample_airbnb

```
db.listingsAndReviews.find({"amenities.0": "Internet"}, {_id: 1})
```


