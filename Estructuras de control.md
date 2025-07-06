
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

``ỳtho