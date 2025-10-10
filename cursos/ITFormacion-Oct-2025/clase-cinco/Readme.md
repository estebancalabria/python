# Clase Cinco - 10 de Octubre 2025

## Valores Thruthy y Falsie

Expresiones Thruthy (Que evaluan a True)
*  Un numero distinto de cero
*  Un string con longitud > 0
*  Lista con elementos. Ejemplo [1,2,3]
*  Diccionario no vacio : Ejemplo {"a":1}
*  Tuplas con elementos : Ejemplo (1,2,3)

Expresiones Falsie (Que evaluan a False)
* El 0
* Un string vacio
* Lista Vacia
* Diccionario Vacio
* Tuplas vacias : ()
* None

## Entornos virtuales

* Cuando ejecuto un archivo.py y me falta instalar una libreria me lanza la excepcion ModuleNotFound
'''
ModuleNotFoundError: No module named 'kivy.app'; 'kivy' is not a package
'''
* Eso me da un indicion de que deberia instalar un paquete con pip install
* Cuando una hace **pip install** instala un modulo (libreria / paquete) para toda la computadora
* Muchas veces (sobre todo cuando hay proyectos que usan una version y otros que usan otra) no es deseable instalar el modulo para toda la computadora sino que lo quiero solamente para mi proyecto
* Entorno virtual es cuando mi proyecto de python utiliza sus prompias librerias independientes de las instaladas para la computadora
* Siempre que vos te bajas un proyecto en pythos desde internet conviene ejecutarlo en un entorno virtual aparte para que no interfiera con las librerias que tenes instaladas en la computadora
* Para crear un entorno virtual vamos a utilizar el siguiente comando
```cmd
python -m venv [Nombre-Entorno]
```
* Al a hacer eso se crea una carpeta con el nombre del entorno donde ahi si van las librerias que van a usarse en el proyecto
* Nota : Puedo tener todos los entornos virtuales que dese por proyecto
* Una vez que creamos el entorno hay que habilitarlo
```cmd
.\[Nombre-Entorno]\Scripts\activate
```
* Una vez que instale la librerias se van a instalar para ese entorno exclusivamente (no para toda la computadora)
```cmd
pip install [paquete que quiero instalar]
```
* La lista de paquetes que una aplicacion necesita se guarda en un archivo llamado requirements.txt
* Muchas veces cuando un proyecto tiene muchas librerias en vez de instalarlas una por una se hace pip install requirements.txt
* El nombre **requirements.txt** es un nombre estandar que adopto la industria de python como archivo donde guardar las librerias que necesita un proyecto
* Para generar el archivo requirements.txt
```cmd
pip freeze > requirements.txt
```
* Existen otras alternativas para crear entornos viruales por ejemplo conda
  * https://anaconda.org/anaconda/conda
* Para salir de entorno
```
deactivate
```


# Modulos, paqueres e imports

* En la practica nadie hace un proyecto en un solo archivo.py extenso sino que lo separa en varios modulos.
* Por ejempo puedo tener este archivo llamado matematicas.py
```python

def sumar(a, b):
    return a + b

PI = 3.14159
```
y usarlo desde otro archivo



- ## Importarlo Directamente
```python
import matematicas

print(matematicas.sumar(5, 3))
```

- ## Importarlo con alias
```python
import matematicas as mt

print(mt.sumar(5, 3))
```

Generarlmente hay librerias populares que tiene un alias que de conocido
* import nunpy as np
* import pandas as pd
* import tensoflow as tf


- ## Importar elementos especificos
```python
from matematicas import sumar

resultado = sumar(5, 3)
print(f"El resultado de la suma es: {resultado}")
```

- ## Nombres en los modulos

* Cada modulo tiene una variable especial independiente que se llama __name__
* Si el modulo se ejecuta por linea de comandos su nomnre es "__main__" sino es directamente le nombre del archivo
* Por eso van a ver muchas veces en pythos
```python
if __name__ == "__main__":
   #El codigo que quiero que se ejecute solamente si es un programa principal
```
