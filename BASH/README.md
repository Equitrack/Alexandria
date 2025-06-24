## BASH 

La bash (Bourne Again Shell) es un intérprete de comandos de Linux bastante versátil para hacer operaciones en servidores.

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

### Bucles y estructuras de control

Condicionales

```bash
#!/bin/bash

if [ condición ]; then
	# Código ejecutado si la condición es verdadera
elif [ condición ]; then
	# Código ejecutado si la segunda condición es verdadera
else
	# Código ejecutado si ninguna condición es verdadera
fi
```

Bucles

```bash
#/bin/bash

# Búcle FOR
for variable in lista_de_elementos; do
	# Código a ejecutar en cada iteración
done
```