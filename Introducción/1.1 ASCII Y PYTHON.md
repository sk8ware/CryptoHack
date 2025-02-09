
La criptografía moderna implica código, y el código implica codificación. CryptoHack ofrece una buena oportunidad para perfeccionar tus habilidades.  
  
De todos los lenguajes de programación modernos, Python 3 se destaca como ideal para escribir rápidamente scripts y ataques criptográficos. Para obtener más información sobre por qué creemos que Python es tan bueno para esto, consulta las [Preguntas frecuentes](https://cryptohack.org/faq#python3) .  
  
Ejecuta el script de Python adjunto y mostrará tu bandera.  
  
**Archivos del desafío:**  
  - [great_snakes.py](https://cryptohack.org/static/challenges/great_snakes_35381fca29d68d8f3f25c9fa0a9026fb.py)  
  
**Recursos:**  
  - [Descarga de Python](https://wiki.python.org/moin/BeginnersGuide/Download)


----

# Resolución:

---

## **1️⃣ Explicación línea por línea**

```python
#!/usr/bin/env python3
```

- **Shebang**: Indica que el script debe ejecutarse con Python 3.

```python
import sys
# import this
```

- **Importa `sys`**: Se usa para verificar la versión de Python.
- **`# import this`**: Está comentado, pero si se descomenta, imprime el "Zen de Python" (principios del lenguaje).

```python
if sys.version_info.major == 2:
    print("You are running Python 2, which is no longer supported. Please update to Python 3.")
```

- **Comprueba si se está usando Python 2** (que ya está obsoleto).
- **Si es así, imprime un mensaje de advertencia**.

```python
ords = [81, 64, 75, 66, 70, 93, 73, 72, 1, 92, 109, 2, 84, 109, 66, 75, 70, 90, 2, 92, 79]
```

- **Lista de números enteros (`ords`)**: Representan caracteres en código ASCII, pero están cifrados.

```python
print("Here is your flag:")
```

- **Muestra un mensaje en pantalla**.

```python
print("".join(chr(o ^ 0x32) for o in ords))
```

- **Descifra el mensaje usando una operación XOR (`^`) con `0x32` (hexadecimal de 50 en decimal)**.
- **`chr(o ^ 0x32)`**: Convierte cada número de la lista en un carácter ASCII después de aplicar la operación XOR.
- **`"".join(...)`**: Une los caracteres en una cadena de texto legible.

---

## **2️⃣ ¿Cómo funciona la operación XOR (`^`)?**

La clave aquí es el uso de **XOR (`^`) con 0x32**.

La operación XOR tiene estas propiedades clave:

- **A ^ B = C**
- **C ^ B = A** (deshaciendo el cifrado)
- **C ^ A = B** (otra forma de revertirlo)

Aquí, cada número en `ords` ha sido **cifrado aplicando XOR con `0x32` (50 decimal)**. Para **descifrarlo**, aplicamos XOR con la misma clave nuevamente.

---

## **3️⃣ Vamos a descifrarlo en Python**

Puedes probarlo en tu máquina copiando y pegando este código en Python:

```python
ords = [81, 64, 75, 66, 70, 93, 73, 72, 1, 92, 109, 2, 84, 109, 66, 75, 70, 90, 2, 92, 79]

decoded_flag = "".join(chr(o ^ 0x32) for o in ords)
print("Here is your flag:")
print(decoded_flag)
```

Cuando lo ejecutes, te mostrará el mensaje oculto. ¡Avísame qué resultado obtienes! 🚀