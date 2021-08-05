# Terraform

## Struktur im Dateisystem
Dateien mit den Endungen:
  * `*.tf`, 
  * `*.tfvars`,
  * `*.tf.json`
werden beim Aufruf selbstständig von Terraform eingelesen

## Sprachelemente
### Provider


### Variablen
#### Definition
```
variable "<name>" {
  description = "<description>"
  type        = "<type>"
  default     = "<default-value>"
}
```



### Ressource
```
ressource "<name>" {
  ...
}
```

### Module
```
# Im Dateisystem
module "<name>" {
  source            = "<path/to/module/directory>"
  <variable_name_1> = <variable_value_1>
  <variable_name_2> = <variable_value_2>
  <variable_name_3> = <variable_value_3>
}
```

### Output
```
# Ressource
output "<name>" {
  value = <ressource>.<ressource_name>.<variable>
}


# Data
output "<name>" {
  value = data.<data_name>.<variable>
}
```


## Aufruf
### Grundlagen
```
$ terraform <parameter>
```

| Parameter | Beschreibung |
| --- | --- |
| `init` | Initialisiert die Umgebung (Download der benötigten Module) |
| `plan` | Zeigt an welche Schritte ausgeführt werden |
| `apply` | Anwendung der Ressourcen |

### Nützliches

