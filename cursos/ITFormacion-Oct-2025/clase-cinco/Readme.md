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
* 
