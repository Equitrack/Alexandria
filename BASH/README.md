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

Comando **read**.

```bash
#!/bin/bash

echo -e "Ingresa tu nombre: \c"
read nombre
echo "Tu nombre es: $nombre"
```

Argumentos.

```bash
#!/bin/bash

echo "El primer argumento es: $1"
echo "El segundo argumento es: $2"
```

### Bucles y estructuras de control

Condicionales para valores numéricos usando corchetes **[ ]**:

| Operador | Significado               | Traducción        |
| -------- | ------------------------- | ----------------- |
| `-eq`    | **equal**                 | Igual a           |
| `-ne`    | **not equal**             | Distinto de       |
| `-gt`    | **greater than**          | Mayor que         |
| `-ge`    | **greater than or equal** | Mayor o igual que |
| `-lt`    | **less than**             | Menor que         |
| `-le`    | **less than or equal**    | Menor o igual que |
```bash
#!/bin/bash

variable_uno=10
variable_dos=10

if [ "$variable_uno" -ne "$variable_dos" ]; then
	# Código ejecutado si la condición es verdadera
elif [ "$variable_uno" -eq "$variable_dos" ]; then
	# Código ejecutado si la segunda condición es verdadera
else
	# Código ejecutado si ninguna condición es verdadera
fi
```

Condicionales para valores numéricos usando paréntesis dobles **((  ))**:

```bash
#!/bin/bash

variable_uno=10
variable_dos=20

if (( variable_uno < variable_dos )) then
	# Código ejecutado si la condición es verdadera
	echo "La variable uno es menor"
else
	# Código ejecutado si ninguna condición es verdadera
	echo "La variable uno NO es menor"
fi
```

Condicionales para cadenas usando corchetes dobles **[[]]**:

| Operador | Significado                               |
| -------- | ----------------------------------------- |
| `==`     | Igual                                     |
| `!=`     | Distinto                                  |
| `<`      | Menor en orden lexicográfico (alfabético) |
| `>`      | Mayor en orden lexicográfico              |
| `-z`     | Longitud cero                             |
| `-n`     | Longitud no cero                          |
```bash
#!/bin/bash

# Variables alfanuméricas
nombre1="apple10"
nombre2="apple2"

# Comparar si son iguales
if [[ "$nombre1" == "$nombre2" ]]; then
  echo "Los nombres son iguales"
else
  echo "Los nombres son diferentes"
fi

# Comparar cuál es menor en orden lexicográfico
if [[ "$nombre1" < "$nombre2" ]]; then
  echo "$nombre1 es menor que $nombre2 en orden alfabético"
else
  echo "$nombre1 es mayor o igual que $nombre2 en orden alfabético"
fi

# Combinación de condiciones con AND y OR
if [[ "$nombre1" != "$nombre2" && "$nombre1" > "$nombre2" ]]; then
  echo "$nombre1 es diferente y mayor que $nombre2"
fi

```

Bucles

```bash
#/bin/bash

# Búcle FOR - Itera la lista
for variable in lista_de_elementos; do
	# Código a ejecutar en cada iteración
done

while [ condicón ]; do
	# Código a ejecutar en cada iteración
done
```

