# Inleiding
“Programming today is a race between software engineers striving to build bigger and better idiot-proof programs, and the Universe trying to produce bigger and better idiots. So far, the Universe is winning.”
 - Rick Cook

Gebruikers doen niet altijd wat je verwacht (en eerlijk is eerlijk: als programmeur is het ook niet altijd te overzien op welke manieren je code gebruikt gaat worden, die maken ook fouten), dus de kans dat er tijdens de uitvoering van een programma wel eens een fout optreedt is groot.
Dit is op zichzelf geen ramp, als er maar op een goede manier mee wordt omgegaan in de code. Een programma dat er halverwege mee ophoudt met een of andere obscure error die de gebruiker niet snapt is altijd een slechte zaak. De oplossing: Error handling
Het basisprincipe van error handling is eigenlijk vrij eenvoudig:
* Je moet erop verdacht zijn welke delen van je code tot fouten kunnen leiden bij (verkeerd) gebruik.
* Aan deze delen voeg je een speciale pythonconstructie toe die de fouten “vangt”.
* Bij het “vangen” van een fout, schrijf je code die voorkomt dat het programma crasht op de fout.
* Eventueel voorzie de je de gebruiker van nuttige feedback (duidelijke foutmelding) zodat deze actie kan ondernemen.

### Opdracht 9
Laten we eerst maar eens wat dingen expres mis laten lopen om een beetje een gevoel te krijgen wat er zoal stuk kan gaan.

 Voer de volgende opdrachten uit en noteer wat de foutmelding is. Probeer ook te begrijpen wat de foutmelding zegt en leg uit wat er precies mis gaat.
