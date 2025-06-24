## BASH 

Bourne Again Shell

La bash es un intérprete de comandos de Linux bastante versátil para hacer operaciones en servidores.

### Variables

Bash se encarga de definir el tipo de variables.

```bash
#!/bin/bash

# Texto
nombre="Alejandro"

# Número
edad=25
year=2025

# Arreglo
frutas=("manzana" "sandía" "plátano")
frutas[3]="limón"

echo "Tu nombre es: $nombre, tu año de nacimiento es el: $((year - edad)), tus frutas favoritas son: ${frutas[@]}"
```

Las variables puedes ser globales o locales (alcance), las locales se definen dentro de una función.

```bash
#!/bin/bash

funcion_ejemplo() {
	local variable_local="soy local"
	echo $variable_local
}

variable_global="Soy global"
funcion_ejemplo
echo $variable_global
```

### Entradas de usuarios

Comando **read**

```bash
#!/bin/bash

echo -e "Ingresa tu nombre: \c"
read nombre
echo "Tu nombre es: $nombre"
```

Argumentos

```bash
#!/bin/bash

echo "El primer argumento es: $1"
echo "El segundo argumento es: $2"
```