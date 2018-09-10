# reveal.js

## Installation
Die Anleitung geht davon aus das node.js bereits installiert ist
```
# Klonen von dem reveal.js-Projekt
$ git clone https://github.com/hakimel/reveal.js.git

# Nachinstalieren der benötigten Module
$ cd reveal.js
$ npm install
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

## Konfiguration

