
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
### Operadores de Asignación

Los operadores de **asignación** sirven para asignar valores a las variables de manera eficiente. Aquí te dejo los más comunes:

| Operador | Descripción                                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------------------------- |
| `=`      | Asignación simple: Asigna el valor a la variable. Ejemplo: `x = 5`                                                        |
| `+=`     | Suma y asigna: Suma el valor de la derecha a la variable de la izquierda. Ejemplo: `x += 2` es equivalente a `x = x + 2`. |
| `-=`     | Resta y asigna: Resta el valor de la derecha a la variable de la izquierda.                                               |
| `*=`     | Multiplica y asigna: Multiplica la variable por el valor de la derecha y asigna el resultado.                             |
| `/=`     | Divide y asigna: Divide la variable por el valor de la derecha y asigna el resultado.                                     |
| `//=`    | División entera y asigna: Realiza la división entera y asigna el resultado.                                               |
| `%=`     | Módulo y asigna: Asigna el residuo de la división de la variable por el valor de la derecha.                              |
| `**=`    | Potencia y asigna: Eleva la variable a la potencia del valor de la derecha y asigna el resultado.                         |
### Operadores de Identidad

Los operadores de **identidad** verifican si dos objetos son **el mismo objeto** en memoria:

|Operador|Descripción|
|---|---|
|`is`|Verifica si dos objetos son el mismo objeto en memoria (no si son iguales).|
|`is not`|Verifica si dos objetos no son el mismo objeto en memoria.|
### Operadores de Membresía

Los operadores de **pertenencia** verifican si un valor está contenido dentro de una secuencia, como una lista o un diccionario:

|Operador|Descripción|
|---|---|
|`in`|Verifica si un valor está presente en una secuencia.|
|`not in`|Verifica si un valor no está presente en una secuencia.|
