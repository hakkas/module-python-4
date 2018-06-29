# Classes

In OOP draait alles om classes (klassen) en objects/instances (objecten of instanties).

Je hebt al eerder met objecten leren werken, maar in deze lesbrief gaan we meer de diepte in. Een class kunnen we zien als een soort sjabloon. Of een malletje … een blauwdruk. En een object is een _instantie_ van dat sjabloon.

Laten we even met het voorbeeld van een persoon verder gaan. We maken een class genaamd Persoon.

```python
class Persoon:
    def __init__ (self, _leeftijd):
        self.leeftijd = _leeftijd

    def printLeeftijd(self):
        print ("Ik ben " + str(self.age) + " jaar oud!")
```

Functies die in een class worden gedefinieerd worden _methoden_ genoemd. In dit geval hebben we twee methodes:
* De ```__init__()``` methode
* en de ```printLeeftijd()``` methode.

De ```__init__()``` methode is een bijzondere. Het is namelijk een constructor: de methode die automatisch wordt aangeroepen zodra je een object van het type Persoon aanmaakt. Methoden krijgen altijd de parameter self mee. Self is een referentie naar het object zelf. Je kunt natuurlijk ook andere parameters opgeven. Die komen na self. In dit geval hebben we de constructor de parameter ```_age``` meegegeven. Dus als we een object van het type Persoon instantiëren, dan moeten we een leeftijd opgeven. Dat wordt dan opgeslagen in de property (eigenschap) self.age.

Het instantiëren van een object van het type Persoon doen we zo:

```python
henk = Person(36)
henk.printLeeftijd()
```
We roepen ook nog even de methode ```printLeeftijd()``` aan.

Laten we onze class uitbreiden. Stel dat we ook de naam van een persoon willen opslaan. En het beroep dat iemand uitoefent. Onze class ziet er nu zo uit:

```python
class Persoon:
  def __init__ (self, _leeftijd, _naam, _beroep):
    self.leeftijd = _leeftijd
    self.naam = _naam
    self.beroep = _beroep

  def printLeeftijd(self):
    print ("Ik ben " + str(self.leeftijd) + " jaar oud")

  def printBeroep(self):
    print ("Ik ben " + self.beroep + " van beroep")

  def printNaam(self):
    print ("Ik heet " + self.naam)

  def printAlles(self):
    print ("Ik ben " + self.naam + " en ben " + str(self.leeftijd) + " jaar oud en ben " + self.beroep + " van beroep!")

henk = Persoon(36, "Henk", "software ontwikkelaar")
henk.printLeeftijd()
henk.printNaam()
henk.printBeroep()
henk.printAlles()
```
We hebben er 4 methodes aan toegevoegd. Het leuke is dat ik natuurlijk meerdere objecten kan maken van het type Persoon. Hier een voorbeeld:

```python
henk = Persoon(36, "Henk", "software ontwikkelaar")
luuk = Persoon(13, "Luuk", "game developer")
jurre = Persoon(13, "Jurre", "game artist")

henk.printAlles()
luuk.printAlles()
jurre.printAlles()
```
Je programmeert zo'n class dus een keer en je kunt er meerdere instanties van maken.

Bekijk ook het volgende filmpje met een voorbeeld en uitleg over de basics van Python classes:

{%youtube%}POQIIKb1BZA{%endyoutube%}

Hierin leer je:
* Basis class syntax (schrijfwijze)
* Class variables
* Class functions (+self)
* Instanties (objects) maken
* Het maken van meerdere instanties (objects) van een klasse en het gebruik ervan


## init() en methoden met parameters

Bij het maken van een nieuw object is het vaak handig als meteen een stukje code wordt uitgevoerd dat de startwaarden van het object goed instelt. Hiertoe dient de speciale ```__init__()``` methode. Methodes kunnen natuurlijk (net als gewone functies) meerdere parameters hebben. Bekijk het volgende filmpje:

{%youtube%}G8kS24CtfoI{%endyoutube%}

Hierin leer je:
* Werking van de speciale ```__init__()``` functie bij classes
* (extra) parameters naast self voor functies

## Standaard waarden voor functieparameters

Zoals je weet heeft een functie parameters. Dat zijn de waarden die je de functie _meegeeft_ als je hem gebruikt (aanroept). Dit geldt zowel voor functies die onderdeel zijn van een class als voor gewone functies. Voor de duidelijkheid een simpel voorbeeld:

```python
def telop (a,b):
  return a+b
```

In het voorbeeld zijn a en b de parameters. Een aanroep van de functie zou nu kunnen zijn:
```python
telop(10,86)
```
En als antwoord zal de waarde 96 worden teruggegeven. In de aanroep hierboven is dus voor a de waarde 10 en voor b de waarde 86 opgegeven. De functie gebruikt de opgegeven waarden in zijn code.
Soms kan het handig zijn om voor een functie een of meerdere _standaardwaarden_ op te geven voor de parameters. Hiermee geef je de aanroeper van de functie de mogelijkheid om enkele parameters “leeg” te laten. Hiervoor wordt dan de standaardwaarde gebruikt. Een voorbeeld maakt dit duidelijk:

```python
def telop (a,b=20):
  return a+b
```

In dit voorbeeld is in de functiedefinitie de waarde 20 als standaardwaarde opgegeven voor parameter b.  Als we nu het volgende doen:
```python
telop(10,86)
```

Krijgen we nog steeds hetzelfde antwoord: 96. Maar als we de waarde voor b weglaten als volgt:
```python
telop(10)
```
Krijgen we als antwoord 30. Python verwacht 2 parameters, maar omdat er maar 1 gegeven is, gebruikt hij deze als waarde voor a en kiest hij de standaardwaarde (20) voor b. Simpel toch?

Let op: Als een functie zowel parameters _met_ standaardwaarde heeft als parameters _zonder_ standaardwaarde, dan moeten de parameters _met_ standaardwaarde altijd achteraan. Zie:

* def voorbeeld(a=10,b,c=20) is fout.
* def voorbeeld(b,a=10,c=20) is goed.

Als je er even over nadenkt, dan is dat logisch. Stel je hebt de (foute) functiedefinitie van (1) en je doet de volgende aanroep:

```python
voorbeeld(13,14)
```
Bedoel je nu dat a gelijk moet zijn aan 13, b aan 14 en c aan zijn standaardwaarde 20? Of bedoel je dat a gelijk is aan zijn standaardwaarde 10, b gelijk aan 13 en c gelijk aan 14? Dit is onduidelijk en dus niet toegestaan.

Als je de definitie van (2) hebt, dan is de aanroep wel duidelijk:

```python
voorbeeld(13,14)
```

Dit betekent nu dat b gelijk is aan 13, a gelijk aan 14 en c gelijk aan zijn standaardwaarde 20.

## Class variables en instance variables
Er zijn verschillende termen voor variabelen die in een class gebruikt worden:
* Class variables: Variabelen die in de klasse definitie worden gezet. De waarde hiervan is dus hetzelfde voor alle objecten (instanties) van deze klasse.
* Instance variables: Variabelen die gemaakt worden in de ```__init__()``` methode van de klasse. Deze verschillen van waarde bij verschillende objecten (instanties) van deze klasse. (Vandaar ook de naam, instance variabelen hebben voor elke instance een unieke waarde)

Niet super lastig, maar belangrijk om deze termen te kennen en uit elkaar te kunnen houden. Bekijk het volgende filmpje voor een korte uitleg met een voorbeeld:

{%youtube%}qSDiHI1kP98{%endyoutube%}
