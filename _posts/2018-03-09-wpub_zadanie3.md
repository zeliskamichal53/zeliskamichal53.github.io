---
layout: post
title: "Zadanie 3"
date: 2018-04-29
categories: FIIT
deadline: 2018-05-02 23:59
permalink: /my-study/WPUB/zadanie3/
zdroj: https://wiki.fiit.stuba.sk/study/bc/info/wp/2017-18/zadanie3/
---
## <a href="{{ page.zdroj }}">XML prezentácia</a>
____
## Splnené požiadavky:
 - opis dokumentu je pomocou DTD v súbore presentation.xml
 <br/> <br/>
   Root element je **presentation**, ktorý musí obsahovať **prvý slajd(first_slajd)** a **posledný slajd(last_slajd)** a môže obsahovať 
   **stredný slajd(middle_slajd)**, v ktorom
   môže byť ľubovoľný počet **obyčajných slajdov(next_slajd)**.
   Prvý slajd musí obsahovať **nadpis(title)**, **podnadpis(subtitle)** a **autora(autor)**.
   Posledný slajd musí obsahovať **nadpis(poďakovanie)** a môže obsahovať **obrázok(picture)**.
   Obyčajné slajdy môžu obsahovať **nadpis(title)**, **obrázok(picture)** a **text(text)**.
   Text sa skladá z ľubovoľného počtu **odrážok(odrazka)**, pričom odrážka môže mať **atribút textformating** pričom povolené hodnoty tohto atribútu sú:
   **bold** - odrážka bude boldom, **italic** - odrážka bude kurzívou, **link** - odrážka bude odkazom napr. na webstránku.
   Obrázok môže mať **popis(popis)**, ktorý sa zobrazí pod obrázkom a musí mať atribúty: **url** - cesta k obrázku, **height** - výška obrázku, 
   **width** - šírka obrázku.
   
 - ukážková prezentácia je v súbore presentation.xml

 - XSL transformácia do xhtml je v súbore toXHTML.xsl, parametrizácia je v súbore parametres.xsl
<br/> <br/>
	**Parametre:**
	- číslovanie strán on/off
	- veľkosť písma všetkých html elementov v prezentácií(h1,h2,p,li), každé sa dá nastaviť samostatne
    - farba písma h1 a h2, každé sa dá nastaviť samostatne   
	- farba pozadia prezentácie
	- fonty písma h1,h2,p,li (každé samostatne)
	
- každý slajd je v samostatnom html súbore v priečinku presentation_in_xhtml. V tomto priečinku je aj css k prezentácií (**presentation.css**) v zložke CSS.
	
## Nesplnené požiadavky	
- XSL transformácia do pdf 	
	
   

 
 