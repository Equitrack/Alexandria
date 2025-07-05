
# PYTHON

Python es un lenguaje de programación interpretado, versátil, amigable y popular, con el que se pueden hacer muchas automatizaciones. 

Variables: python se encarga de definir automaticamente el tipo de datos.

## Estructura de datos

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