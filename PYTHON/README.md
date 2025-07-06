
# PYTHON

Python es un lenguaje de programación interpretado, versátil, amigable y popular, con el que se pueden hacer muchas automatizaciones. 

Características:

- Tipado dinámico
- Gestión automática de memoria
- Multiplataforma
- Multiparadigma
- Gran ecosistema de bibliotecas
- Comunidad activa

Temario:

**Fundamentos:**

- Variables y tipos de datos
- Operadores y bucles
- Entrada y salida de datos
- Estructura de datos
- Funciones
- Manejo de excepciones
- Manejo de archivos
- Manejo de memoria
- Módulos y bibliotecas

# Variables

- Tipos de datos básicos: enteros, flotantes, cadenas de texto, booleanos.
- Tipos de colecciones: listas, tuplas, diccionarios, conjuntos.

# Operadores

- Operadores aritméticos, lógicos y de comparación.
- Operadores de asignación, identidad y membresía.

### Operadores Aritméticos

| Operador | Descripción                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `+`      | Suma: Suma dos valores.                                                                              |
| `-`      | Resta: Resta el valor de la derecha del valor de la izquierda.                                       |
| `*`      | Multiplicación: Multiplica dos valores.                                                              |
| `/`      | División: Divide el valor de la izquierda por el valor de la derecha (siempre devuelve un flotante). |
| `//`     | División entera: Divide y devuelve el cociente entero (sin decimales).                               |
| `%`      | Módulo: Devuelve el residuo de la división.                                                          |
| `**`     | Potencia: Eleva un número a la potencia de otro (ej. `2 ** 3` es igual a 8).                         |
### Operadores Lógicos

| Operador | Descripción                                                                                              |
| -------- | -------------------------------------------------------------------------------------------------------- |
| `and`    | AND lógico: Retorna `True` si ambos operandos son verdaderos.                                            |
| `or`     | OR lógico: Retorna `True` si al menos uno de los operandos es verdadero.                                 |
| `not`    | NOT lógico: Invierte el valor de verdad del operando (si es `True` lo convierte en `False` y viceversa). |
### Operadores de Comparación

| Operador | Descripción                                                                                    |
| -------- | ---------------------------------------------------------------------------------------------- |
| `==`     | Igualdad: Verifica si los dos valores son iguales.                                             |
| `!=`     | Desigualdad: Verifica si los dos valores son diferentes.                                       |
| `>`      | Mayor que: Verifica si el valor de la izquierda es mayor que el de la derecha.                 |
| `<`      | Menor que: Verifica si el valor de la izquierda es menor que el de la derecha.                 |
| `>=`     | Mayor o igual que: Verifica si el valor de la izquierda es mayor o igual que el de la derecha. |
| `<=`     | Menor o igual que: Verifica si el valor de la izquierda es menor o igual que el de la derecha. |

# Estructuras de control


# Estructura de datos

| Tipo         | Descripción                                                                                                     |
| ------------ | --------------------------------------------------------------------------------------------------------------- |
| Listas       | Es un conjunto de datos en un solo lugar, estos elementos pueden ser de diferentes tipos (números, cadenas ...) |
| Diccionarios | Con un conjunto de datos clave-valor, se accede a los valores usando la clave.                                  |
| Tuplas       | Son listas pero no se pueden modificar.                                                                         |
| Conjuntos    | Son listas que no permiten valores duplicados.                                                                  |
 > Los arreglos como en C, tienen un tamaño definido, no son dinámicos y con el mismo tipo de datos.
 
 Listas

```python
# Definir una lista
servidores = ["servidor1", "servidor2", "servidor3", "servidor4"]

# Acceso
print(servidores[1]) # Imprime servidor2

# Agregar un elemento
servidores.append("servidor5")

# Eliminar un elemento
servidores.remove("servidor3")

# Modificar
servidores[2] = "servidor_reemplazado"
```

Diccionarios

```python
# Definir diccionario

servidor = {
	"nombre": "servidor1",
	"ip": "192.168.1.1",
	"estado": "activo"
}

# Acceso
print (servidor["ip"]) # Imprime 192.168.1.1

# Agregar
servidor["sistema_operativo"] = "Linux"

# Eliminar
del servidor["estado"]

# Actualizar
servidor["estado"] = "inactivo"

```

Tuplas

```python
# Definir tupla
estado = ("activo", "inactivo", "indefinido")

# Acceso
print(estado[0]) # imrpime activo
```

Conjuntos (no tienen un índice como las listas)

```python
# Definir 
direcciones_repetidas = {"10.10.10.1", "10.10.10.2", "10.10.10.3", "10.10.10.1"}
print(direcciones_repetidas) # imprime {'10.10.10.1', '10.10.10.2', '10.10.10.3'}

# Agregar
direcciones_repetidas.add("10.10.10.4")

# Eliminar - muestra un error si no existe
direcciones_repetidas.remove("10.10.10.5")

# Eliminar - no muestra un error si no existe
direcciones_repetidas.discard("10.10.10.5")
```