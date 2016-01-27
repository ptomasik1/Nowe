###Zadanie 1a MongoDB

Do zadania wybralem miesieczna baze danych z postow reddita z kwietnia 2015
Nazwa pliku: RC_2015-01

#####Najpierw musialem zmienic domyslny katalog dla bazy mongoDB, gdyz wirtualne maszyny chmury Microsoft maja male dyski zamontowane pod rootem /
Dodalem symboliczy link:

```sh
sudo service mongodb stop
sudo mv mongodb /mnt/mongodb/
sudo ln -s /mnt/mongodb/ /var/lib/mongodb
sudo chown mongodb:mongodb /mnt/mongodb/
sudo service mongodb start
```

#####Import pliku bazy danych Reddit RC_2015-01 do bazy MongoDB wersja 3.0.7



```sh
time bunzip2 -c RC_2015-05.bz2 | mongoimport --drop --host 127.0.0.1 -d test -c reddit
```
Sredni czas importu to ok 7000 pozycji na sekunde.
Procesor obciazoy byl w ~80%. Obciazone byly 4 procesory jednoczesnie, zwykle pierwsze. Niestety dane diagnostyczne zostaly skasowane chmurze i mam tylko zrzuty ekranów komendy top:





