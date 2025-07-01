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

while [ condición ]; do
	# Código a ejecutar en cada iteración
done
```

### Manejo de errores

Existen los códigos de estado que nos indican cuál es la razón de fallo en un scrip o si este terminó de forma existosa, lo más populares son estos 3:

| Código de Salida | Significado                     | Descripción                                            |
| ---------------- | ------------------------------- | ------------------------------------------------------ |
| 0                | Éxito                           | El comando o script terminó correctamente.             |
| 1                | Error genérico                  | Fallo general o sin una causa específica.              |
| 2                | Mal uso de la línea de comandos | Error en los argumentos o sintaxis del comando/script. |

Los comandos **set** y **trap** son muy útiles para manejar errores y señales.

```bash
#!/bin/bash

# Activa la salida inmediata ante errores
set -e

# Código
echo "Inicio de código, sin errores"

# Desactivar la salida ante errores
set +e

# Activar la salida inmediata ante erres y fallos en tuberías (pipes)
set -o pipefail -e

# No se permiten errores en tuberías
echo "Mensaje de texto" > documento.txt

cat documento.txt | grep "texto"

# Activar modo depuración
set -x

```

```bash
#!/bin/bash

function handle_error() {
	local error_code=$?
	local error_line=$BASH_LINENO
	local error_command=$BASH_COMMAND
	echo "Error en la linea $error_line: $error_command (código de salida $error_code)"
	exit 1
}

trap handle_error ERR

# Ejemplo de un comando que puede fallar

cat /ruta/no/existente.txt

echo "Este mensaje no se mostrará si hay un error anterior"
``` 

```bash
#!/bin/bash

# Redirige la salida (si tiene errores) a un archivo, es importante cuidar el espacio entre el código de estado y ">"

ls /ruta/no/existente 2> error.txt
```

### Seguridad en los scripts

- Validar las entradas del usuario para prevenir ataques como inyección de código

```bash
#!/bin/bash

# Validar que existe un archivo

read -p "Introduce el nombre del archivo:" filename

if [[ ! -e "$filname"]]; then
	echo "Archivo no encontrado o entrada inválida."
	exit 1
fi
```

- Evitar usar directamente la entrada del usuario

```bash
#!/bin/bash

entrada_sucia="rm -rf / ; echo 'hola' && uname -a"
entrada_limpia=$(echo "$entrada_sucia" | sed 's/[^a-zA-Z0-9_-]//g')

echo "Entrada original: $entrada_sucia"
echo "Entrada sanitizada: $entrada_limpia"

# OUTPUT
Entrada original: rm -rf / ; echo 'hola' && uname -a
Entrada sanitizada: rm-rfechoholauname-a
```

- Asegurar la seguridad del entorno

```bash
set -euf -o pipefaill

# -e Termina el script si un comando falla
# 
```