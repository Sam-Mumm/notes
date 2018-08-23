# Shell-Programmierung
Die nachfolgenden Notizen wurden auf der Basis der kornshell erstellt, sollten aber auch mit anderen üblichen Shells wie bash funktionieren

## besondere Variable
| Variable | Inhalt |
| -- | -- |
| $1 - $9 | übergebene Parameter an das Skript |
| $0 | Name des Skripts |
| $? | Rückgabewert (Exit-Code) des Scripts |
| $# | Anzahl der übergebenen Parameter |
| $$ | Prozess-ID |
| $* | Zeichenkette mit den übergebenen Parametern |
| $@ | Zeichenkette mit den übergebenen Parametern |
| shift | Shift auf die übergebenen Parameter $3 -> $2, $2 -> $1 usw. |
| $! | Prozess-ID des letzten ausgeführten Befehls |

## Tests
### ... auf Zahlen
```
((zahl1 <operator> zahl2))
```

gültige Operatoren sind:
 * ==
 * !=
 * <, >, >=, <=

### ... auf Zeichenketten
```
[[string1 <operation> string2]]
```
gültige Operatoren sind
 * ==
 * !=

### Schalter
| Test | Liefert true wenn...
| -- | -- |
| -z string | der String eine Länge von 0 hat |
| -n string | der String eine Länge ungleich 0 hat |
| -a Objekt | es existiert |
| -f Objekt | es ein symbolischer Link oder eine Datei ist |
| -d Objekt | es ein Verzeichnis ist |
| -c Objekt | ein character special file ist |
| -b Objekt | ein block special file ist |
| -p Objekt | eine named pipe ist |
| -S Objekt | ein Socket ist |
| -L Objekt | ein symbolischer Link ist |
| -k Objekt | für das Objekt das sticky bit gesetzt ist |
| -s Objekt | das Objekt nicht leer ist |
| -r Objekt | das Objekt lesbar ist |
| -w Objekt | das Objekt schreibar ist |
| -x Objekt | das Objekt ausführbar ist |
| -O Objekt | der Benutzer der das Skript ausführt auch Besitzer des Objekts ist |
| -G Objekt | der Benutzer der das Skript ausführt in der gleichen Gruppe wie das Objekt ist |
| -u Objekt | für das Objekt das set-user-id-Bit gesetzt ist |
| -g Objekt | für das Objekt das set-group-id-Bit gesetzt ist |
| Objekt1 -nt Objekt2 | Wenn das Änderungsdatum von Objekt1 aktueller ist, als von Objekt2 |
| Objekt1 -ot Objekt2 | Wenn das Änderungsdatum von Objekt1 älter ist, als von Objekt2 |

## Kontrollstrukturen
### if-then-else
```
# Einfach
if <logischer Ausdruck>
then
	<command>
fi

# Geschachtelte
if <logischer Ausdruck>
then 
	<command>
else if <logischer Ausdruck>
      	<command>
fi
fi
```


### switch-case
```
case <wert> in
	<pattern1>) <command1> ; ... ; <commandN>;;
	<pattern2>) <command1> ; ... ; <commandN>;;
	...
	<patternN>) <command1> ; ... ; <commandN>;;
```

## Schleifen
### while
```
while( <logischer Ausdruck>)
do
	<rumpf>
done
```
### for

## Funktionen
```
<funktionsname>()
{
	<command>
}

<funktionsname>
```
