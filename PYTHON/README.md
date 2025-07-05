
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

# Elimianr
del servidor["estado"]

# Actualizar
servidor["estado"] = "inactivo"

```