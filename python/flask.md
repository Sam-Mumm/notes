# Flask

**benötigtes Paket:** flask

## Dateien und Verzeichnisse
### Verzeichnisstruktur
Die Verzeichnisse
 * `bin`
 * `include`
 * `lib`
 * `local`
werden durch die Installation von flask erstellt
 
```
flask/
  ├─ bin
  ├─ include
  ├─ lib
  ├─ local
  └─ app
  	  ├─ __init__.py
	  ├─ routes.py
	  ├─ static
	  │   ├─ js
	  │   │   └─ bootstap.min.js
	  │   └─ css
	  │   	  ├─ screen.css
	  │       └─ bootstrap.min.css
	  └─ templates
		  └─ index.html
```

### app/\__init__.py
```
from flask import Flask

app = Flask(__name__)

from app import routes
```

### app/routes.py
```
from app import app
from flask import render_template

@app.route('/')
def index():
    user="John Doe"

    return render_template('index.html', username=user)
```

### app/templates/index.html
```
<html>
    <head>
        <link rel= "stylesheet" type= "text/css" href= "{{ url_for('static',filename='css/bootstrap.min.css') }}">
        <link rel= "stylesheet" type= "text/css" href= "{{ url_for('static',filename='css/screen.css') }}">

    </head>
    <body>
        <div class="wrapper">
            <nav id="sidebar">
                <div class="sidebar-header">
                    <h2>Wiki</h2>
                </div>

                <ul class="list-unstyled components">
                    <li>
                        <a href="#ansible" data-toggle="collapse" aria-expanded="false" class="dropdown-toggle">Pages</a>
                        <ul class="collapse list-unstyled" id="menu">
                            <li><a href="#">Subpage 1</a></li>
                            <li><a href="#">Subpage 2</a></li>
                        </ul>
                    </li>
                </ul>
            </nav>

            <div id="content">
                <h1>Hallo, {{username}}</h1>
            </div>
        </div>
        <script src="{{ url_for('static',filename='js/bootstrap.min.js') }}"></script>
    </body>
</html>
```