---
layout: post
title: "Zadanie 1"
date: 2018-03-11
categories: FIIT
deadline: 2018-03-11 23:59
permalink: /my-study/WPUB/zadanie1/
zdroj: https://wiki.fiit.stuba.sk/study/bc/info/wp/2017-18/zadanie1/
---

## <a href="{{ page.zdroj }}">Osobná webová prezentácia na GitHub pages</a>
____
## Dokumentácia

Stránka obsahuje 5 layout-ov:
 - default.html
 - home.html
 - post.html
 - predmet.html
 - zoznam_predmetov.html
 
### default.html
 Defaultný layout, ktorý je použitý vo všetkých ostatných layout-och. Obsahuje hlavičku a pätičku stránky, ktoré sú v layout-e zahrnuté pomocou
 tagu include.
 {% highlight html %}{% raw %}
 <body> 
    {% include header.html %}    
    <div class="wrapper">
      <section>
        {{ content }}
      </section>
    </div>	
	{% include footer.html %}	
  </body>
 {% endraw %}{% endhighlight %} 
#### header.html
 Hlavička obsahuje navigačný panel, ktorý je vytváraný pomocou dátového súboru nav_panel v zložke _data.
{% highlight html %}{% raw %}
<div id="header">
        <nav>    				
			{% for link in site.data.nav_panel.nav_panel %}
				{% assign url = link.url %}
				<li class="fork"><a href={{ url }}>{{ link.name }}</a></li>
			{% endfor %}						    		
        </nav>
      </div>
{% endraw %}{% endhighlight %}
#### footer.html
Pätička obsahuje moje meno, odkaz na jekyll oficiálnu stránku a github použitého CSS.
{% highlight html %}{% raw %}
<div id="footer">
		<nav>
		<li class="downloads"> &copy; {{ site.author }} - Powered by <a href="https://jekyllrb.com">Jekyll</a>, CSS by <a href="https://github.com/pages-themes/midnight">midnight</a> </li>
		</nav>      
      </div>
{% endraw %}{% endhighlight %}	  
### home.html
 Layout vytvorený na domovskú stránku. Obsahuje defaultný layout includnutý vo front matter, ktorý je rozšírený o nadpis a popis stránky, ktoré
 sú ťahané zo súboru config.yml pomocou premennej site. Taktiež obsahuje tag content, ktorý je v prípade ak existuje markdown súbor v zložke posts 
 s rovnakou cestou ako home bude nahradený obsahom tohoto súboru. Na spodku je zobrazený čas pomocou site.time, ktorý zobrazuje kedy bola stránka 
 naposledy aktualizovaná.
 {% highlight html %}{% raw %}
 <div>
  <div id="title">
          <h1>{{ site.title }}</h1>
          <p>{{ site.description }}</p>
          <hr>
        </div>	
</div>
{{ content }} 
<br><br><br>
<hr>
<div>
<p align="right">
Posledná aktualizácia stránky {{ site.time | date: "%-d/%m/%Y" }} o {{ site.time | date: "%T" }} 
</p>
</div>
{% endraw %} {% endhighlight %}
### post.html 
 Layout, ktorý oproti default-nému zobrazuje navyše názov stránky(príspevku) a dátum uložený vo front matter pomocou premenných page.title a page.date.
 page.date je upravený pomocou | date: date_to_string.
 {% highlight html %}{% raw %}
 <h1>{{ page.title }}</h1>
<p class="meta">{{ page.date | date_to_string }}</p>
<div class="post">
  {{ content }}
</div>
{% endraw %}{% endhighlight %}
### predmet.html
 Layout, ktorý slúži na zobrazenie názvu predmetu ako nadpis stránky pomocou premennej page.title. 
 {% highlight html %}{% raw %}
 <div>
  <div id="title">
          <h1>{{ page.title }}</h1>
          <hr>
        </div>	
  {{ content }} 
</div>
{% endraw %}{% endhighlight %}
### zoznam_predmetov.html
 Layout na vypísanie všetkých predmetov z dátového súboru study.yml v zložke _data za použita for cyklu a if podmienky na vytvorenie klikateľného odkazu v prípade, že 
 existuje url predmetu. 
 {% highlight html %}{% raw %}
{% for semester in site.data.study reversed %}
{{ semester.semester }}	 
	<ul>
	{% for predmet in semester.predmety %}		
		{% if predmet.url %}
			<li>{{ predmet.skratka }} - <a href={{ predmet.url }}>{{ predmet.name }}</a></li>
		{% else %}
			<li>{{ predmet.skratka }} - {{ predmet.name }}</li>
		{% endif %}					   
	{% endfor %}				  
	</ul>	
{% endfor %}{% endraw %}{% endhighlight %} 

## Použité premenné (niektoré sú použité vo viacerých súboroch, nie len v uvedených)
- v defaultnom layout-e je použité: site.lang
- v pätičke site.author
- v layout-e home sú použité site.time, site.title, site.description
- v layout-e post a predmet page.title, page.date
- v dokumentácií zadania 1 wpub_zadanie1.md page.zdroj
- v súbore wpub.md site.posts, page.permalink 

## Použité pluginy
 - jekyll-youtube: použitý na stránke Hobby hobby.md {% highlight html %}{% raw %}{% youtube "https://www.youtube.com/watch?v=zPyyo8_Ndyo" %}{% endraw %}{% endhighlight %}
 - jekyll-maps: použitý na stránke About about.md {% highlight html %}{% raw %}{% google_map zoom="8" width="650" src="_data/places.yml" %}{% endraw %}{% endhighlight %}
 Po nahratí stránky na github tieto pluginy nie sú funkčné a aby bolo možné stránku zobraziť online bez nich, treba tieto riadky zakomentovať pomocou liquid tagov comment a endcomment

## Použité dátové súbory
 - nav_panel.yml - obsahuje dáta potrebné na vytvorenie navigačnej lišty v hlavičke stránky(url a meno)
 - places.yml - obsahuje lokácie, ktoré sú následne zobrazené na google mape na stránke About
 - study.yml - obsahuje predmety(názov, skratka, url), ktoré sú vypísane na stránke Moje štúdium
 
## Použité filtre a tagy
 - Tagy: v tejto dokumentácií sú použité tagy highlight, raw, v defaultnom layout-e je tag include, v layout-e zoznam_predmetov sú použité konštrukcie if a for (tie sú vo viacerých súboroch)
 - Filtre: <br>
v defaultom layout-e je filter na jazyk stránky {% highlight html %}{% raw %}<html lang="{{ site.lang | default: "sk" }}">{% endraw %}{% endhighlight %}
v layout-e home je použitý filter na dátum {% highlight html %}{% raw %}{{ site.time | date: "%-d/%m/%Y" }} o {{ site.time | date: "%T" }}{% endraw %}{% endhighlight %}
v layout-e post je dátum transformovaný na string {% highlight html %}{% raw %}<p class="meta">{{ page.date | date_to_string }}</p>{% endraw %}{% endhighlight %}
filter na výpis najnovších príspevkov zo zložky _posts 
{% highlight html %}{% raw %}
<u1>
{% assign vsetko = site.posts | sort: 'date' %}
{% for post in vsetko reversed %}
	<li><a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date_to_string }}</li>
	<br>
{% endfor %}
</u1>
{% endraw %}{% endhighlight %}
 
 