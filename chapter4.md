

# Inleiding
> “Programming today is a race between software engineers striving to build bigger and better idiot-proof programs, and the Universe trying to produce bigger and better idiots. So far, the Universe is winning.”

Rick Cook

Gebruikers doen niet altijd wat je verwacht (en eerlijk is eerlijk: als programmeur is het ook niet altijd te overzien op welke manieren je code gebruikt gaat worden, die maken ook fouten), dus de kans dat er tijdens de uitvoering van een programma wel eens een fout optreedt is groot.
Dit is op zichzelf geen ramp, als er maar op een goede manier mee wordt omgegaan in de code. Een programma dat er halverwege mee ophoudt met een of andere obscure error die de gebruiker niet snapt is altijd een slechte zaak. De oplossing: _Error handling_

Het basisprincipe van error handling is eigenlijk vrij eenvoudig:
* Je moet erop verdacht zijn welke delen van je code tot fouten kunnen leiden bij (verkeerd) gebruik.
* Aan deze delen voeg je een speciale pythonconstructie toe die de fouten _vangt_.
* Bij het “vangen” van een fout, schrijf je code die voorkomt dat het programma crasht op de fout.
* Eventueel voorzie de je de gebruiker van nuttige feedback (duidelijke foutmelding) zodat deze actie kan ondernemen.

Laten we eerst maar eens wat dingen expres mis laten lopen om een beetje een gevoel te krijgen wat er zoal stuk kan gaan.

Maak hiervoor opdracht 9 in repl.it!

Je hebt nu een aantal foutmeldingen uitgeprobeerd. Er zijn er nog (heel) veel meer (kijk voor de grap maar eens naar de hele [lijst](https://docs.python.org/3/library/exceptions.html)). Dat python onderscheid maakt tussen zoveel verschillende foutmeldingen is een goede zaak. Zoals we gaan zien kun je fouten “vangen” en afhandelen. Hierbij kun je verschillende soorten fouten op een verschillende manier behandelen en voor elke fout de juiste oplossing inbouwen.


## Exceptions
Ìn de vorige paragraaf heb je (expres) een aantal fouten veroorzaakt. Het optreden van zo’n fout heet in Python een Exception (uitzondering). Deze exceptions kun je “vangen” en zorgen dat ze op een nette manier worden afgehandeld in plaats van met een cryptische foutmelding en een onderbroken programma. Bekijk het volgende filmpje:

{%youtube%}1cCU0owdiR4{%endyoutube%}

Hierin leer je:
* Try block
* Catch blok met specifieke Exceptions
* Catch blok met algemene Exceptions
* Finally block

Maak nu opgave 9 in repl.it.
