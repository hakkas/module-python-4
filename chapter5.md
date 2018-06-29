
### Opdracht 9
 Voer de volgende opdrachten uit en noteer wat de foutmelding is. Probeer ook te begrijpen wat de foutmelding zegt en leg uit wat er precies mis gaat.
a) Voer de volgende code uit. Wat gaat er mis en waarom?

```python
lijst = [1, 2, 3]		
 print (lijst[6])
```

b) Voer de volgende code uit. Geef verschillende getallen als invoer. Probeer dan ook eens het getal 0 als invoer. Wat gaat er mis en waarom?

```python
deler = int(input("Met hoeveel personen ga je een taart delen? "))
 stuk = 1.0 / deler 
print ("Dan krijgt iedereen", stuk, "stuk taart")
```

c) Voer de code uit vraag b nog eens uit, maar in plaats van een getal voer je een stuk tekst in zoals “appeltaart”. Wat gaat er mis en waarom?

d) Voer de volgende code uit. Voer verschillende getallen in. Het werkt niet, waarom? (kijk goed naar de foutmelding):

```python
getal = input("Geef een getal: ") 
uitkomst = 2 + getal
 print ("De uitkomst is:", uitkomst)
```

e) Leg uit wat er mis gaat bij het maken van het nieuwe object mijnTaart:

```python
class Appeltaart:      
  calorieen = 2500      

  def __init__(self, aantal_stukken):         
    self.stukken = aantal_stukken  

mijnTaart = Appeltaart()   
```

Je hebt nu een aantal foutmeldingen uitgeprobeerd. Er zijn er nog (heel) veel meer (kijk voor de grap maar eens naar de hele [lijst](https://docs.python.org/3/library/exceptions.html)). Dat python onderscheid maakt tussen zoveel verschillende foutmeldingen is een goede zaak. Zoals we gaan zien kun je fouten “vangen” en afhandelen. Hierbij kun je verschillende soorten fouten op een verschillende manier behandelen en voor elke fout de juiste oplossing inbouwen.
