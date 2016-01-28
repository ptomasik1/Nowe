## Egzamin, Przemyslaw Tomasik

Pobralem baze danych brytyjskich restauracji i zaimportowalem standardowo (tym razem bez rozpakowywania do bazy danych):

```sh
time mongoimport -d restaurancje -c restauracje < restaurants.json
```
Proces skonczyl sie szybko:

```sh
connected to: 127.0.0.1
imported 2548 objects
0.13user 0.02system 0:00.68elapsed 23%CPU (0avgtext+0avgdata 61088maxresident)k
4792inputs+0outputs (33major+1801minor)pagefaults 0swaps
```

Sprawdzmy, czy dziala. Wyswietlam pierwszy rekord, licze rekordy itp:


Wyswietle najpierw restauracje w miastach, ktorych nazwa zaczyna sie na "L".

```sh
db.restauracje.find({"address line 2": /^L/}, {_id: 0, name: 1, rating: 1, type_of_food: 1, "address line 2": 1}).sort({name: 1}).limit(5)

{ "address line 2" : "London", "name" : "042 Restaurant & Bar", "rating" : 3, "type_of_food" : "African" }
{ "address line 2" : "London", "name" : "042 Restaurant & Bar", "rating" : 3, "type_of_food" : "African" }
{ "address line 2" : "London", "name" : "042 Restaurant & Bar", "rating" : 3, "type_of_food" : "African" }
{ "address line 2" : "London", "name" : "109 Ristorante", "rating" : 5, "type_of_food" : "Pizza" }
{ "address line 2" : "Leeds", "name" : "1pizza1", "rating" : 4, "type_of_food" : "Pizza" }
```
Sprawdzmy zatem jeszcze 5 afrykanskich restauracji:

```sh
> db.restauracje.find({type_of_food: "African"},{_id: 0}).limit(5)
{ "URL" : "http://www.just-eat.co.uk/restaurants-042-restaurant-e11/menu", "address" : "885 High Road Leytonstone", "address line 2" : "London", "name" : "042 Restaurant & Bar", "outcode" : "E11", "postcode" : "1HR", "rating" : 3, "type_of_food" : "African" }
{ "URL" : "http://www.just-eat.co.uk/restaurants-042-restaurant-e11/menu", "address" : "885 High Road Leytonstone", "address line 2" : "London", "name" : "042 Restaurant & Bar", "outcode" : "E11", "postcode" : "1HR", "rating" : 3, "type_of_food" : "African" }
{ "URL" : "http://www.just-eat.co.uk/restaurants-042-restaurant-e11/menu", "address" : "885 High Road Leytonstone", "address line 2" : "London", "name" : "042 Restaurant & Bar", "outcode" : "E11", "postcode" : "1HR", "rating" : 3, "type_of_food" : "African" }
{ "URL" : "http://www.just-eat.co.uk/restaurants-280degreesafrican-nw6/menu", "address" : "280 Kilburn High Road", "address line 2" : "London", "name" : "280 Degrees African & Nigerian Restaurant", "outcode" : "NW6", "postcode" : "2BY", "rating" : 2.5, "type_of_food" : "African" }
{ "URL" : "http://www.just-eat.co.uk/restaurants-280degreesafrican-nw6/menu", "address" : "280 Kilburn High Road", "address line 2" : "London", "name" : "280 Degrees African & Nigerian Restaurant", "outcode" : "NW6", "postcode" : "2BY", "rating" : 2.5, "type_of_food" : "African" }

```













