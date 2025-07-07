
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

- Variables y tipos de datos
- Operadores
- Estructuras de control
- Funciones
- Manejo de sesiones
- Manejo de archivos
- Manejo de memoria
- Módulos y bibliotecas

# Variables

- Tipos de datos básicos: enteros, flotantes, cadenas de texto, booleanos.
- Tipos de colecciones: listas, tuplas, diccionarios, conjuntos.

# Operadores

- Operadores aritméticos, lógicos y de comparación.
- Operadores de asignación, identidad y membresía.
- Precedencia de operadores.
# Estructuras de control

- Condicionales: `if`, `else`, `elif` (siempre se usan paréntesis).
- Bucles: `for`, `while`, `break`, `continue`.
- Manejo de excepciones: `try`, `except`, `finally`.
# Estructura de datos

- Listas
- Diccionarios
- Tuplas
- Conjuntos
- Strings

# Estructuras de Datos

- Listas, tuplas, diccionarios, y conjuntos: operaciones básicas.
- Manipulación de cadenas de texto: indexado, slicing, métodos útiles.
- Comprensión de listas y otras colecciones.

# Funciones

- Definición de funciones: parámetros, retorno de valores.
- Funciones lambda y anónimas.
- Funciones recursivas.
- Ámbito y visibilidad de variables.

# Manejo de Sesiones

- Variables locales y globales.
- Espacios de nombres y scopes en funciones.
- Uso de `global` y `nonlocal`.
# Manejo de Archivos

- Leer y escribir archivos con diferentes modos (`r`, `w`, `a`, `b`).
- Uso de `with` para manejo automático de archivos.
- Archivos binarios y de texto.

# Manejo de Memoria

- Gestión automática de memoria: referencias y recolector de basura.
- Comprensión de cómo funcionan las referencias de objetos.
- Evitar fugas de memoria con buenas prácticas.
- Iteradores vs generadores (yield)

```python
# Usar un generador para leer un archivo línea por línea
def leer_archivo_linea_por_linea(nombre_archivo):
    with open(nombre_archivo, 'r') as archivo:
        for linea in archivo:
            yield linea.strip()

# Ejemplo de uso
for linea in leer_archivo_linea_por_linea('archivo_grande.txt'):
    print(linea)
```

# Módulos y Bibliotecas

- Importación de bibliotecas estándar y de terceros.
- Uso de **pip** para instalar paquetes.
- Creación de módulos personalizados.
- Bibliotecas populares (por ejemplo, `math`, `os`, `sys`, `datetime`, `json`).

```
os: Permite interactuar con el sistema operativo, como trabajar con archivos y directorios.

sys: Proporciona acceso a variables y funciones que interactúan con el entorno del sistema, como los argumentos de la línea de comandos o la salida estándar.
```


