---
title: 'Maandag 15 april: vicieuze-BIOS-cirkel'
author: Merlijn Sebrechts
layout: post
date: 2013-04-17
url: /?p=208
categories:
  - Tanzania

---
Ik toon de bibliotheekapplicatie aan de bib-guy en hij lijkt er zeer content over. Hij ziet het zitten om er mee te werken. Tijdens de demonstratie vind ik echter nog wat foutjes. Ik kan ze niet direct oplossen want het internet werkt niet.

Verkenningstocht: waarom werkt het internet niet? In het kantoor van Bernard merk zie ik dat de schakelaar van het stopcontact van de router uit staat. Dat is het probleem dus! Ik zet de schakelaar aan, internet werkt! 5 minuten later valt de elektriciteit uit&#8230; -_-

Jeroen laat me vanuit aqua lodge weten dat de generator weer stilgevallen is. Volledig kigoma krijgt electriciteit van een grote generator die op “oil” draait. Die generator staat dicht bij aqua lodge dus we horen die ronken (en stilvallen).

5 minuten later: Terug elektriciteit. 5 minuten later: Terug uit. En zo verder en verder voor de hele voormiddag. Ik moet er geen tekeningskes bij maken dat ik nietveel heb kunnen doen&#8230;

In de namiddag zijn de elektriciteit en internet beiden terug.
  
**Waarschuwing:** Het volgende deel is zeer technisch en volgens mij onverstaandbaar voor een computerleek. Mama, vraag maar veel uitleg aan Papa!

In de namiddag krijg ik 2 kapotte computers in mijn handen gestopt die zo dringend mogelijk gefixt moeten worden. Eén start er niet meer op, blijft hangen in de BIOS. De BIOS zegt dat de Harde schijf en de diskette-drive kapot zijn. De andere computer &#8220;has no icons&#8221;. Maw: de gebruikersaccount is corrupt waardoor windows met een tijdelijk profiel aanmeld. Op dat tijdelijk profiel is het bureaublad leeg&#8230;

Computer 1:
  
Deze computer heeft geen diskette-drive, natuurlijk denkt de BIOS dat hij kapot is. Ik laat de BIOS weten dat hij geen diskette-drive heeft en probleem 2 is weg. Ik wil kijken of harde schijf echt kapot is dmv een linux-live-cd. De computer heeft enkel een cd-speler terwijl ik enkel DVD&#8217;s heb; via een bootable usb dan maar. Probleem: BIOS versie heeft geen ondersteuning voor bootable usb&#8217;s. Ik moet de BIOS dus updaten.

BIOS updaten doe je op 2 manieren:
  
1) vanuit windows zelf [aangezien windows niet opstart is dit geen optie]
  
2) via diskette [computer heeft geen diskette-drive,, geen optie]

Ik download de driver terwijl ik in de brolcontainer ga gaan zoeken achter een werkende diskette-drive. Die vind ik niet, maar ik vind wel een werkende DVD-drive, waardoor ik toch mijn linux-live-dvd kan opstarten! Ik steek de dvd-drive in de computer, steek de dvd in de drive en start de computer op met knoppix (een linux versie).

De harde schijf heeft 2 partities: 1 ntfs van 15GB met windows er op en 1 kapotte partitie van 15GB met niets er op. Ik verwijder de kapotte partitie en voeg de vrije ruimte toe aan de eerste partitie. Nu heeft de computer een werkende harde schijf van een goeie 30GB. Fantastisch! Ik sluit linux af en probeer windows op te starten. Ik eet mijn stoel op uit frustratie omdat de computer nog steeds niet wil opstarten. Hij is wel gestopt met zeggen dat de harde schijf kapot is.

Pruts, Gepruts, Gevloek, Gepruts.

Uitendelijk vind ik een manier om windows toch op te starten. Als je ergens in de BIOS de herstelpartitie probeert op te starten dan start windows normaal. Dit is echter een veel te omslachtige manier om het een oplossing te kunnen noemen. Maar nu kan ik tenminsten de BIOS al updaten. Misschien is het daarmee opgelost? Computer herstarten, Hopen, Frustreren. Uit pure miserie begin ik met de boot-order te prutsen; de cdromdrive eerst zetten enzo.. Plots zie ik dat er naast de cdromdrive een vinkske staat en naast de harde schijf niet. Ik zie beneden tussen de commando&#8217;s staan &#8220;press space to enable the hard drive&#8221;. Zou dit het zijn?

Voor de laatste keer: Computer uitschakelen, Computer aanzetten, Hopen&#8230;. BAM! Een Bom van euforie blaast de helft van de kamer weg.

Het probleem was dus: Een lokale &#8220;computer genious&#8221; had er niets beter op gevonden dan de harde schijf uit te zetten in de boot-order. Ze stond er in, ze stond op de eerste plaats; maar ze stond gewoon uit. Tot vandaag wist ik niet dat je dit kon doen. Waarom je dit zou willen doen, God weet het, maar ik ben alleszins zeer content dat ik het gevonden heb&#8230;

tl;dr: pruts,pruts,success!