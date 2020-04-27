# jq

*Homepage:* https://stedolan.github.io/jq/

## Suchen


## Erstellen
```
#!/bin/bash
sendung="Sesamstrasse"
lied='der|die|das'

json=$( ./jq -n \
             --arg name "$sendung" \
             --arg intro $lied \
             '{sendung: $name, reim: ($intro|split("|")) }' )

echo $json
```

