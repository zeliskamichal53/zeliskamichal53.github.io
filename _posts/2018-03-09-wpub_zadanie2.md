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
Na vypracovanie tohto zadania som si vybral časť bakalárskej práce zo Slovenskej poľnoshopodárskej univerzity v Nitre.
Štandardné členenie textu bolo dosiahnuté pomocou elementov &lt;chapter&gt; - kapitola, &lt;section&gt; - podkapitoly, &lt;appendix&gt; - dodatok,
&lt;para&gt;, &lt;literallayout&gt;. 
Obsah bol generovaný automaticky
z uvedených elementov. Na generovanie zoznamu tabuliek a obrázkov som do súboru thesis.xsl dopísal figure a table na riadok:
{% highlight xml %}
<xsl:param name="generate.toc">
book title,toc,figure,table
</xsl:param> 
{% endhighlight %}
Na zvýraznenie slov som použil element &lt;emphasis&gt;, ktorý defaultne zvýrazňuje kurzívou a na zvýraznenie bold-om som pridal
atribút bold: &lt;emphasis role="bold"&gt;. Na členenie textu odrážkami alebo číslovaním som použil element &lt;orderedlist numeration="loweralpha"&gt; a
následne element &lt;listitem&gt;.
Odkazy na url boli spravené pomocou elementu &lt;ulink&gt; s atribútom url. Odkazy na vlastné časti sa v dokumente nenachádzali, ale ich
implementácia (uvedená nižšie) by bola rovnaká ako v prípade odkazov na obrázky, tabuľky a zdroje. 
Na odkaz pod čiarou som použil element &lt;footnote&gt;, avšak iba ako ukážku, pretože v pôvodnej práci sa poznámka pod čiarov nenachádzala.
Na zoznam použitej literatúry boli použité elementy &lt;bibliography> a &lt;bibliomixed id="..."&gt; s ID-ečkom kvôli odkazovaniu v texte na zdroj, 
pomocou elementu &lt;xref linkend="..." /&gt;. Vo výsledom dokumente nie sú citované a uvedené všetky zdroje, pretože v pôvodnej práci ich je 
veľmi veľa a ich implementácia by bola rovnaká. 
Tabuľky som vytváral pomocou elementu &lt;table&gt; s atribútom ID kvôli odkazom v texte pomocou &lt;xref&gt; (rovnako ako pri citovaní zdrojov).
Následne bola použita klasická konštrukcia pomocou elementov &lt;tgroup&gt;, &lt;thead&gt;, &lt;tbody&gt;, &lt;row&gt;.
Obrázky som vkladal pomocou elementu &lt;figure&gt; taktiež s atribútom ID kvôli odkazovaniu cez xref. Vo &lt;figure&gt; elemente
som ešte použil elementy &lt;mediaobject&gt;, &lt;imageobject&gt; a následne element &lt;imagedata&gt; s atribútom cesty k obrázku.
Na vytvorenie indexu som použil element &lt;index/&gt; pred prvou kapitolou, ktorý automaticky vytvoril zoznam indexovaných pojmov.
Tieto pojmy som indexoval pomocou elementov &lt;indexterm&gt; a následne v prípade primárneho &lt;primary&gt; a v prípade sekundárneho pomocou &lt;secondary&gt;.
Na trasformáciu do výsledného formátu pdf som použil poskytnutú šablónu zo stránky predmetu.
Pri písaní xml súboru som narazil na problém pri ktorom som nemohol uviesť do podkapitoly 4.4.1.1 pod obázok 4.1 ďaľšie 2 tabuľky,
pretože pri spustení .bat súboru na preklad zamrzol na riadku Making portrait pages on A4 paper (210mmx297mm) a nebol schopný dokončiť
pomocný súbor fo.xml.

 
 