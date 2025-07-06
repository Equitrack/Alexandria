
# Estructuras de control

## Manejo de excepciones

En Python, el manejo de excepciones se realiza con tres bloques principales:

- **`try`**: Este bloque contiene el código que podría generar una excepción. Python intentará ejecutar este código.
-  **`except`**: Si se produce una excepción dentro del bloque `try`, el código dentro de `except` se ejecuta para manejar el error.  
- **`finally`**: Este bloque, si está presente, siempre se ejecuta después del bloque `try` y `except`, sin importar si ocurrió una excepción o no. Es útil para liberar recursos, cerrar archivos, etc.

```python
try:
    # Intentar ejecutar código que podría generar una excepción
    resultado = 10 / 0  # Esto generará una excepción de división por cero
except ZeroDivisionError:
    # Si ocurre una excepción de tipo ZeroDivisionError, este bloque se ejecutará
    print("No se puede dividir por cero")
finally:
    # Este bloque se ejecutará siempre, independientemente de si hubo excepción o no
    print("Bloque finally ejecutado")
```

```python
def dividir(a, b):
    try:
        resultado = a / b
    except ZeroDivisionError:
        print("Error: No se puede dividir por cero")
    except TypeError:
        print("Error: Ambos valores deben ser números")
    else:
        print(f"El resultado de la división es: {resultado}")
    finally:
        print("Operación completada")

dividir(10, 2)  # Ejecución correcta
dividir(10, 0)  # Error de división por cero
dividir(10, "a")  # Error de tipo
```

### **Tipos comunes de excepciones**:

- **`ZeroDivisionError`**: Ocurre cuando intentas dividir por cero.
- **`TypeError`**: Se produce cuando se realiza una operación en un tipo de dato incorrecto.
- **`FileNotFoundError`**: Cuando intentas abrir un archivo que no existe.
- **`ValueError`**: Ocurre cuando un valor no es del tipo esperado.

Se pueden definir una excepción personalizada.

