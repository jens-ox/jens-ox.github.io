---
title: Kostenlos Webseite einrichten
date: 2017-12-09 17:30:00
categories: jekyll
---

Bisher hab ich meine Webseite entweder selber geschrieben oder ein CMS wie [Ghost](https://ghost.org/) verwendet. Das hatte folgende Probleme:

- **Kosten**: Ich musste mich um das Hosting kümmern. Das kostet.
- **Versionierung**: Ist die lokale Seite dieselbe wie die auf dem Server? Das ist natürlich nur bei selbstgeschriebenen Seiten ein Problem.
- **Unnötiger Overhead**: Verwendet man Ghost oder --- noch schlimmer --- Wordpress, so hat man einen massiven Overhead an Kram, den man eigentlich nicht braucht - Verwaltung von Assets, ein Haufen an Extensions und ähnliches, und das alles nur für ein paar einfache Seiten. Braucht man eigentlich nicht.
- **Unnötige Angriffsfläche**: Dadurch, dass man eine ganze Verwaltungsplattform hat, auf der verschiedene Leute Posts und ähnliches erstellen können, hat man auch eine unnötig große Angriffsfläche. Das interessiert mich allerdings nicht allzu sehr, weil auf meinem Server nichts anderes außer meine Webseite liegt.

[Jekyll](https://jekyllrb.com/) versucht diese Probleme zu lösen, besonders in Verbindung mit [Github](https://github.com/):

- **Versionierung**: Die Webseite ist einfach ein besonderes Repository. Versionierung gibt es also geschenkt.
- **Kein Overhead**: Jekyll generiert ganz normale, statische HTML-Seiten. Das bedeutet sehr kurze Ladezeiten und hohe Kompatibilität.
- **Kostenlos**: Mithilfe des [Github Student Pack](https://education.github.com/pack) kann man sich also gratis eine eigene Webseite beschaffen. Dazu muss man nur den kostenlosen private plan von Github nutzen.


## Vorbereitungen

- Neues Repo mit dem Name `[Nutzername].github.io` einrichten (mehr Infos bei [Github Pages](https://pages.github.com/))
- Neue Domain erwerben (über das Github Student Pack kriegt man eine .me-Domain ein Jahr gratis bei Namecheap)

## DNS einrichten

Richtet man keine Extra-Domain ein, so wird die Seite letztendlich unter `[Nutzername].github.io` erreichbar sein.
Falls man sich dafür entscheidet, eine Extra-Domain einzurichten, muss man noch die DNS-Einträge anpassen. Man muss lediglich zwei `A`-Einträge einrichten:

{% include figure image_path="/assets/images/posts/2017-12/Screenshot_2017-12-09_18-27-06.webp" alt="DNSEinrichten" caption="Einrichten der DNS-Einträge bei Namecheap." %}

Anschließend muss man noch die Domain in den Einstellungen des Github-Repos eintragen:

{% include figure image_path="/assets/images/posts/2017-12/github-pages.webp" alt="Github Page einrichten" caption="Eintragen der Domain in den Github Pages-Einstellungen des Repos." %}

Nun muss nur noch Jekyll aufgesetzt werden. Gegebenenfalls muss davor noch Ruby gemeinsam mit gem installiert werden.

## Jekyll einrichten

{% highlight shell %}
~ $ gem install jekyll bundler
~ $ jekyll new my-homepage
~ $ cd my-homepage
~/my-homepage $ bundle exec jekyll share
{% endhighlight %}


Nun ist die aktuelle Version unter `http://localhost:4000/` erreichbar.
Anschließend muss noch git eingerichtet werden:

{% highlight shell %}
~/my-homepage $ git init
~/my-homepage $ git remote add origin https://github.com/[Nutzername]/[Nutzername].github.io
~/my-homepage $ git commit -am "init"
~/my-homepage $ git push -u origin master
{% endhighlight %}

Nun ist die aktuelle Version der Seite auch auf Github (und, falls eingerichtet, auch unter der oben angegebenen Domain) erreichbar. Github kompiliert die Seite selbstständig :blush:

## Jekyll aufhübschen

Das Default-Theme von Jekyll finde ich persönlich ziemlich hässlich. Zum Glück gibt es einen Haufen Themes, die man in den Einstellungen des Github-Repos eintragen kann.

Alternativ kann man ein Theme auf Github forken (ich verwende [Sparrow](https://github.com/lingxz/sparrow)) und das direkt als `[Nutzername].github.io`-Repo verwenden.

Das war's! :smile:
