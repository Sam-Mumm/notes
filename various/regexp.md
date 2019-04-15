# Reguläre Ausdrücke

## Definitionen
| Zeichen | Bedeutung |
|---|---|
| <code>^</code> | Zeilenanfang |
| <code>$</code> | Zeilenende |
| <code>\Z</code> | Maskieren von Zeichen Z |
| <code>.</code> | ein beliebiges Zeichen |
| <code>[...]</code> | ein Zeichen aus der Menge "..." |
| <code>[^...]</code> | kein Zeichen aus der Menge |
| <code>A*</code> | der Ausdruck A kann nicht oder beliebig oft (oder gar nicht) vorkommen |
| <code>A+</code> | der Ausdruck A muss mindestens einmal, kann aber beliebig oft auftreten |
| <code>A?</code> | der Ausdruck A darf einmal auftreten, muss es aber nicht |
| <code>A{N}</code> | der Ausdruck A muss N-mal auftreten |
| <code>A{min,max}</code> | der Ausdruck A muss mindestens `min`-mal und `max`-mal auftreten |


### Zeichenklassen


## Beispiele
#### eMail-Adressen
```
([0-9a-zA-Z]([-.\w]*[0-9a-zA-Z\.])*@([0-9a-zA-Z][-\w]*[0-9a-zA-Z]\.)+[a-zA-Z]{2,9})
```



