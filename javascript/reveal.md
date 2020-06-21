# reveal.js

## Installation und Start
Unabhängig von der Art der Installation sind die Folien nachdem Start des Frameworks unter der URL: `http://localhost:8000` zu erreichen
### Direkt
Die Anleitung geht davon aus das node.js bereits installiert ist
```
# Klonen von dem reveal.js-Projekt
$ git clone https://github.com/hakimel/reveal.js.git

# Nachinstalieren der benötigten Module
$ cd reveal.js
$ npm install
$ npm start
```

### via Docker
```
$ docker pull
```

Um reveal.js in Docker nutzen zu können müssen folgende Verzeichnisse existieren:

```
$ docker start
```



## Grundgerüst
```
<!doctype html>
<html>
	<head>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">

		<title>reveal.js</title>

		<link rel="stylesheet" href="css/reveal.css">
		<link rel="stylesheet" href="css/theme/white.css">

		<!-- Theme used for syntax highlighting of code -->
		<link rel="stylesheet" href="lib/css/zenburn.css">

		<!-- Printing and PDF exports -->
		<script>
			var link = document.createElement( 'link' );
			link.rel = 'stylesheet';
			link.type = 'text/css';
			link.href = window.location.search.match( /print-pdf/gi ) ? 'css/print/pdf.css' : 'css/print/paper.css';
			document.getElementsByTagName( 'head' )[0].appendChild( link );
		</script>
	</head>
	<body>
		<div class="reveal">
			<div class="slides">
					<!--- Folien --->
			</div>
		</div>

		<script src="lib/js/head.min.js"></script>
		<script src="js/reveal.js"></script>

		<script>
			// More info about config & dependencies:
			// - https://github.com/hakimel/reveal.js#configuration
			// - https://github.com/hakimel/reveal.js#dependencies
			Reveal.initialize({
				mouseWheel: true,
				dependencies: [
					{ src: 'plugin/markdown/marked.js' },
					{ src: 'plugin/markdown/markdown.js' },
					{ src: 'plugin/notes/notes.js', async: true },
					{ src: 'plugin/highlight/highlight.js', async: true, callback: function() { hljs.initHighlightingOnLoad(); } }
				]
			});
		</script>
	</body>
</html>
```

## Folien
Als Syntax wird sowohl HTML als auch Markdown unterstützt

###HTML
```
<div class="slides">
	<section>
		<h2> <span class="">Titel der Präsentation</h2>
		<h6>von</h6>
		<h6>Dan</h6>
	</section>

	<section>
		<h2>Agenda</h2>
		<ul>
			<li>Punkt 1</li>
			<li>Punkt 2</li>
			<li>Punkt 3</li>
		</ul>
	</section>
	...
</div>
```


### Markdown
#### in einer externen Datei
```
<section data-markdown="example.md"  
	data-separator="^---"  
	data-notes="^Note:"  
	data-charset="utf-8">
</section>
```

| Parameter | Beschreibung |
| --- | --- |
| ``data-markdown`` | Markdown-Datei |
| ``data-separator`` | regulärer Ausdruck als Trennzeichen zwischen zwei Folien |
| ``data-notes`` | Notizen für den Sprecher |
| ``data-charset`` | Zeichensatz der Folien |


### Designelemente
Die nachfolgenden Designelemente funktionieren sowohlfür Folien die auf HTML als auch auf Markdown basieren.

#### Zwei Spalten
**Quelle:** https://github.com/webpro/reveal-md/issues/223#issuecomment-442401483
##### CSS
```
#left {
    margin: 10px 0 15px 20px;
    text-align: left;
    float: left;
    z-index:-10;
    width:35%;
    font-size: 0.85em;
    line-height: 1.5;
}

#right {
    margin: 10px 0 15px 0;
    float: right;
    text-align: left;
    z-index:-10;
    width:61%;
    font-size: 0.85em;
    line-height: 1.5; 
}
```

##### Folie
```
<div id="left">
    ...
</div>

<div id="right">
    ...
</div>
```

#### Fragemente
**Quelle:** https://couchblog.de/nico/2014/07/praesentationen-mit-reveal-js/
##### HTML
```
<ul>
    <li class="fragment" data-fragment-index="1">Erscheint als erstes</li>
    <li class="fragment" data-fragment-index="2">... und dann dieses</li>
</ul>
```

##### Mardown
```
- Erscheint als erstes <!-- .element: class="fragment" data-fragment-index="1" -->
- ... und dann dieses <!-- .element: class="fragment" data-fragment-index="2" -->
```


#### Unterdrücken von Großbuchstaben in den Überschriften
Einige Themes stellen alle Folien-Überschriften standardmäßig in Großbuchstaben dar. Dies lässt sich wie folgt unterbinden:
```
h1, h2, h3, h4, h5, h6 {
    text-transform: none !important;
}
```


## Konfiguration

