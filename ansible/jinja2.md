# Jinja2

## Kontrollstrukturen
### if-Abfrage
```
{% if <condition> %}
  <ResultA>
{% else %}
  <ResultB>
{% endif %}
```

### Tests
| Tests | Beschreibung
| -- | -- |
| ``even(<value>)`` | Liefert true wenn die Variable gerade ist |
| ``odd(<value>)`` | Liefert true wenn die Variable ungerade ist |

## Schleifen
### for-Schleife
```
{% for <variable> in <array> %}
  {{variable}}
{% endfor %}
```

### Tests
| Tests | Beschreibung
| -- | -- |
| ``loop.index`` | Liefert die Anzahl der bisherigen Durchläufe (beginnend mit 1) |
| ``loop.last`` | Liefert true, wenn es der letzte Schleifendurchlauf ist |
| ``loop.first`` | Liefert true, wenn es der erste Schleifendurchlauf ist |
| ``loop.previtem`` | Liefert das Element vom vorherigen Durchlauf |
| ``loop.nextitem`` | Liefert das Element vom nächsten Durchlauf |


## Beispiel
