---
layout: post
title: "Zadanie 2"
date: 2018-03-25
categories: FIIT
deadline: 2018-03-26 23:59
permalink: /my-study/WPUB/zadanie2/
zdroj: https://wiki.fiit.stuba.sk/study/bc/info/wp/2017-18/zadanie2/
---

## <a href="{{ page.zdroj }}">Transformácia vybraného dokumentu do formátu DocBook</a>
____
## Dokumentácia
{% raw %}
Na vypracovanie tohto zadania som si vybral časť bakalárskej práce zo Slovenskej poľnoshopodárskej univerzity v Nitre.
Štandardné členenie textu bolo dosiahnuté pomocou elementov <chapter> - kapitola, <section> - podkapitoly, <appendix> - dodatok,
<para>, <literallayout>. 
Obsah bol generovaný automaticky
z uvedených elementov. Na generovanie zoznamu tabuliek a obrázkov som do súboru thesis.xsl dopísal figure a table na riadok:
{% highlight xml %}
<xsl:param name="generate.toc">
book title,toc,figure,table
</xsl:param> 
{% endhighlight %}
Na zvýraznenie slov som použil element <emphasis>, ktorý defaultne zvýrazňuje kurzívou a na zvýraznenie bold-om som pridal
atribút bold: <emphasis role="bold">. Na členenie textu odrážkami alebo číslovaním som použil element <orderedlist numeration="loweralpha"> a
následne element <listitem>.
Odkazy na url boli spravené pomocou elementu <ulink> s atribútom url. Odkazy na vlastné časti sa v dokumente nenachádzali, ale ich
implementácia (uvedená nižšie) by bola rovnaká ako v prípade odkazov na obrázky, tabuľky a zdroje. 
Na odkaz pod čiarou som použil element <footnote>, avšak iba ako ukážku, pretože v pôvodnej práci sa poznámka pod čiarov nenachádzala.
Na zoznam použitej literatúry boli použité elementy <bibliography> a <bibliomixed id="..."> s ID-ečkom kvôli odkazovaniu v texte na zdroj, 
pomocou elementu <xref linkend="..." />. Vo výsledom dokumente nie sú citované a uvedené všetky zdroje, pretože v pôvodnej práci ich je 
veľmi veľa a ich implementácia by bola rovnaká. 
Tabuľky som vytváral pomocou elementu <table> s atribútom ID kvôli odkazom v texte pomocou <xref> (rovnako ako pri citovaní zdrojov).
Následne bola použita klasická konštrukcia pomocou elementov <tgroup>, <thead>, <tbody>, <row>.
Obrázky som vkladal pomocou elementu <figure> taktiež s atribútom ID kvôli odkazovaniu cez xref. Vo <figure> elemente
som ešte použil elementy <mediaobject>, <imageobject> a následne element <imagedata> s atribútom cesty k obrázku.
Na vytvorenie indexu som použil element <index/> pred prvou kapitolou, ktorý automaticky vytvoril zoznam indexovaných pojmov.
Tieto pojmy som indexoval pomocou elementov <indexterm> a následne v prípade primárneho <primary> a v prípade sekundárneho pomocou <secondary>.
Na trasformáciu do výsledného formátu pdf som použil poskytnutú šablónu zo stránky predmetu.
Pri písaní xml súboru som narazil na problém pri ktorom som nemohol uviesť do podkapitoly 4.4.1.1 pod obázok 4.1 ďaľšie 2 tabuľky,
pretože pri spustení .bat súboru na preklad zamrzol na riadku Making portrait pages on A4 paper (210mmx297mm) a nebol schopný dokončiť
pomocný súbor fo.xml.
{% endraw %}

 
 