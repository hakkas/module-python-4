# Overerving

Je hebt al gezien dat klassen een handige manier zijn om eenmalig een definitie van iets te schrijven (bijvoorbeeld de Enemy class uit de vorige opgaven) en meerdere objecten te maken die deze definitie gebruiken. Daar kunnen we nog een schepje bovenop doen met het principe van overerving (inheritance in het Engels). Bekijk het volgende filmpje:

{%youtube%}oROcVrgz91Y{%endyoutube%}

Hierin leer je:
* De basics van inheritance (een klasse alle eigenschappen van een andere klasse laten overnemen en hier dingen aan toevoegen)
* Overriding. Dit is het vervangen van een geërfde eigenschap (zoals een functie) door een andere invulling ervan.

Het voorbeeldje uit het filmpje is simpel, maar inheritance is een erg krachtig concept. Je kunt zo een hele stamboom van classes maken die steeds specifieker worden. Hierdoor heb je nergens dubbele code, maar wel veel verschillende bruikbare classes met (deels) andere eigenschappen.

> #### Note::Opgave 6
Maak nu opgave 6 in repl.it

## Methoden van je parent aanpassen

Hoewel het fijn is dat je methoden die je geërfd hebt kunt vervangen, gooi je daarmee soms ook veel nuttige code weg. Je schrijft namelijk de hele methode opnieuw, terwijl je soms gewoon een kleine toevoeging wilt doen aan de geërfde methode.
Om dit te bereiken kun je de code van een methode van je parent weer oproepen als je als kindklasse de methode overschrijft.
Bekijk het volgende voorbeeld:

```Python
class Persoon:

    def __init__(self, voor, achter):
        self.voornaam = voor
        self.achternaam = achter

    def wie_ben_ik(self):
        print "Mijn naam is", self.voornaam, self.achternaam

class Medewerker(Persoon):

    def __init__(self, voor, achter, stafnr):
        Persoon.__init__(self, voor, achter)
        self.stafnummer = stafnr

    def wie_ben_ik(self):
        Persoon.wie_ben_ik(self)
        print "en mijn stafnummer is:", self.stafnummer

x = Persoon("Frits", "Worschtenbroodt")
y = Medewerker("Hendrik", "Appelentaerte", 104)

x.wie_ben_ik()
y.wie_ben_ik()
```

Uitvoer:
```
Mijn naam is Frits Worschtenbroodt
Mijn naam is Hendrik Appelentaerte
en mijn stafnummer is: 104
```

In de code zie je 2 klassen: Persoon en Medewerker.  Medewerker is een kindklasse van Persoon en erft zowel de __init__() methode als de wie_ben_ik() methode van Persoon.

Beide methoden worden in Medewerker overschreven door een nieuwe versie, maar op een andere manier dan tot nu: De code uit de originele methode van de parent wordt hierbij steeds eerst aangeroepen ( ```Persoon.__init__(self, voor, achter)``` en ```Persoon.wie_ben_ik(self))``` en vervolgens worden er nog dingen aan toegevoegd. De schrijfwijze hiervan lijkt op het gewoon aanroepen van een methode met 2 verschillen:
Je noemt de naam van de parent-klasse (in dit geval Persoon) in plaats van de naam van de instantie
De self parameter moet ook worden opgegeven

Bekijk de code goed en zorg dat je goed begrijpt hoe het aanroepen van een methode van de parent werkt.

> #### Note::Opgave 7
Maak nu opgave 7 in repl.it

## Meervoudige overerving
Bij overerving ben je niet beperkt tot 1 parent class. Een nieuwe klasse kan variabelen en functies erven van meerdere klassen tegelijk. Een voorbeeld zie je in het volgende filmpje:

{%youtube%}YCEVvs5BhpY{%endyoutube%}

Hierin zie je:
* Het erven van functies uit 2 verschillende classes
* Een aantal dingen komen nog niet naar voren in het eenvoudige voorbeeld van het filmpje. Multiple inheritance is in sommige gevallen zeker handig, maar kan ook voor nieuwe problemen zorgen.

> #### Note::Opgave 8
Maak nu opgave 8 in repl.it

### Multiple inheritance probleem 1: conflicterende methoden
Bij meervoudige overerving kunnen gemakkelijk conflicten ontstaan. Bekijk het volgende voorbeeldje:

```python
class Papa:
	def zeg_hallo(self):
		print "Hallo!"

class Mama:
	def zeg_hallo(self):
		print "Hoi!"

class Kind(Papa, Mama):
	def slaap(self):
		print "Zzzz"

henkie = Kind()
henkie.zeg_hallo()
```

Hier erft de Kind klasse dezelfde methode van 2 verschillende ouder klassen. Wat zou de uitvoer zijn bij de laatste regel?

Het goede antwoord is “Hallo!”. Bij een conflict zoals hier, worden de parent classes op volgorde bekeken. Omdat de Kind klasse hier als eerste van de Papa class erft (die staat als eerste in zijn lijstje), zal daarvan de zeg_hallo() methode worden overgenomen. Je kunt je voorstellen dat dit voor problemen of verwarring kan zorgen.

### Multiple inheritance probleem 2: meerdere __init__() methoden
Het probleem van conflicterende methoden van de vorige paragraaf wordt nog erger als beide ouders een ```__init__()``` methode hebben. Immers maar 1 van deze __init__() methoden wordt overgenomen door de kindklasse. Hierdoor kunnen zelfs verkeerd ingestelde variabelen ontstaan in de kindklasse. De ```__init__()``` methodes van beide ouders waren er immers niet voor niets. Ze zetten allerlei startwaarden goed en dat gebeurt nu misschien niet meer.
Een manier om dit (deels) te omzeilen is om de Kindklasse een nieuwe ```__init__()``` methode te geven die de ```__init__()``` methoden van beide ouders eerst aanroept. Bijvoorbeeld:

```python
class Kind(Papa, Mama):

    def __init__(self, var1, var2, var3):
        Papa.__init__(self, var1)
        Mama.__init__(self, var2)

        self.nieuwe_waarde = var3
```

Dit is geen garantie tot succes, want misschien spreken de ```__init__()``` functies van de Papa en Mama classes elkaar wel tegen en krijg je dus nog steeds rare dingen
In de praktijk wordt multiple inheritance niet veel gebruikt omdat het (zoals hierboven kort besproken) regelmatig meer problemen introduceert dan het oplost. In sommige specifieke gevallen is het nuttig en het is goed te weten dat het kan, maar wees er voorzichtig mee…
