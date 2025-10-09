# Clase Cuatro - 9 de Octubre del 2025

# Repaso

* Tipos De datos
  * Clases (Tipos de datos defininos por el usuario)
  * Listas
    * Compresiones de lista
* Estructuras de control
  * for
  * if
  * expersiones if ternarias
  * match
* Funciones
  * Parametros
    * Parametros opcionales,
      * Los de tupla * (parametros abiertos)
      * Los de diccinario **
      * Metodos (en una clase)
  * Ciudadanos de primer orden
  * Expresiones Lambda
  * Funciones de orden superior
  * Metaprogramacion / Reflexion
  * Que devolvian varios valores


# Reflection en python

La capacidad de poder inpeccionar un objeto en tiempo de ejecucion y manipular sus y metodos y propiedades a partir de de cadenas
Principalmente tenemos el:
* dir
* getattr

```python
class Persona:
  def __init__(self, nombre, edad):
    self.nombre = nombre
    self.edad = edad

  def saludar(self):
    print(f"Hola, mi nombre es {self.nombre} y tengo {self.edad} años.")

p = Persona("Esteban", 45);

print(dir(p))
print("Los atributos (y metodos) del objeto persona son:")
for atributo in dir(p):
  if not atributo.startswith("__"):
    print(f"{atributo} :  {getattr(p, atributo)} : {type(getattr(p, atributo))}")
```

# Google Colab

* Con el ! adelante podes ejecutar una instruccion en la terminal del colab
* Poniendo %%writefile hola.py al principio  de la celda la podemos guardar en un archivo

# Funciones

## Type Hints

```python
def saludar(nombre : str) -> str:  #No hace nada es para que el programador que lo lea sepa de que tipo se espera el dato
  return f"Hola {nombre}"

def saludar_2(nombre : str):  #No hace nada es para que el programador que lo lea sepa de que tipo se espera el dato
  return f"Hola {nombre}"

def saludar_3(nombre) -> str:  #No hace nada es para que el programador que lo lea sepa de que tipo se espera el dato
  return f"Hola {nombre}"


print(saludar("Esteban"))
print(saludar(3))

# Hay checkeadores que validan que los tipos que esten bien pero es aparte
```
En prinpcipio no hacen nada salvo que lo valides explicitamente 
---
- ### mypy
Con mypy. Primero lo instalo
```cmd
pip install mypy
```
(El colab)
```
!pip install mypy
```
Luego lo ejecuto
```
mypy archivo.py
```

---

- ### typeguard
Promero lo instalo (ya viene instalado en colab)
```cmd
pip install typeguard
```
Luego con el decorador @typechecked (para los metodos que quiero checkear UNO POR UNO)
```python
from typeguard import typechecked

@typechecked                       #decorador como en java, en c# atributos van entre corchetes []    
def saludar(nombre : str) -> str:  #No hace nada es para que el programador que lo lea sepa de que tipo se espera el dato
  return f"Hola {nombre}"

print(saludar(3))
```
esto anterior tira un error
```
TypeError                                 Traceback (most recent call last)
/tmp/ipython-input-153494062.py in <cell line: 0>()
      1 from typeguard import typechecked
```
---
- ### Pydantic
Para el tipado pero solo en la programacion orientada a objetos

> https://docs.pydantic.dev/latest/

```python
from pydantic import BaseModel, ConfigDict

class Persona(BaseModel):
  model_config = ConfigDict(validate_assignment=True)   #Esto es necesario para que valide los tipos de los atributos sino lo hace solo en el constructor
  nombre : str
  edad : int

  ## Me crea el constructor solo

p = Persona(nombre="Esteban", edad=45)
p.nombre = 44             #ValidationError  comentar y descomentar esta linea     
p.edad = "Treinatytress"  #ValidationError  comentar y descomentar esta linea      
print(p)
```

## Decoradores

Decoradores sin parametros
```python
def log(func):
  
  def envoltorio(*args, **kwargs):                     #wrapper en ingles es envoltorio
    print(f"Invocando funcion {func.__name__}")
    resultado = func(*args, **kwargs)
    print(f"Funcion {func.__name__} invodada")
    return resultado
  
  return envoltorio


@log
def saludar(nombre:str):
  print(f"Hola {nombre}")



saludar("Esteban")
```

Decoradores con parametros
```python
ef log(prefijo:str):
  def decorador(func):  
    def envoltorio(*args, **kwargs):                     #wrapper en ingles es envoltorio
      print(f"{prefijo} Invocando funcion {func.__name__}")
      resultado = func(*args, **kwargs)
      print(f"{prefijo} Funcion {func.__name__} invodada")
      return resultado
    
    return envoltorio
  return decorador


@log("-----")
def saludar(nombre:str):
  print(f"Hola {nombre}")



saludar("Esteban")
``

# Iterables

## Funciones para trabajar con Iterables

* map
* filter
* reduce
* max
* min
* sum

---
- ### map

```python
iterable = [1,2,3,4,5,6,5]

print("Compresiones de lista")
#Compresiones de listas
cuadrados =  [el**2 for el in iterable]
print(cuadrados)
print(cuadrados)

print("\nMetodo map")
cuadrados = map(lambda x: x**2, iterable)  #map podemos traducirlo como transformacion
print(f"El map me devuelve una clase especial map: {cuadrados} de tipo {type(cuadrados)}")
# El map devuelve un iterador de solo lectura para adelante 
# Lazy Loading y no duplica los datos en memoria
# Esto es una funcion que usan mucho de  
# El map es lo que se llama un generador

print(list(cuadrados))  # Para mostrarla la tengo que recorrer y la consuo
print(list(cuadrados))  # Ahora si lo vuevlo a recorrer me muestra []

for el in cuadrados:   #Aca no hace nada lo vacie
  print(el)

print(list(cuadrados)) #Aca no hace nada lo vacie
```
es lo mimsmo que hacer
```python
#Lo mismo
iterable = [1,2,3,4,5,6,5]

def cuadrado(x):
  return x*x

cuadrados = map(cuadrado, iterable)  #map podemos traducirlo como transformacion
print(list(cuadrados))
```
---
- ### reduce
```python
from functools import reduce

iterable = range(1,101)
print(f"Iterable {list(iterable)}")

sumatoria = sum(iterable)
print(f"Sumatoria {sumatoria}")

sumatoria = reduce(lambda sumatoria_actual, ultimo_numero: sumatoria_actual + ultimo_numero, iterable)
# La primera la sumatoria_Actual es 0 y el ultimo numero es el 1 
# La segunda vez la sumatoria_Actual es 1 y el ultimo numero es el 2
# La tercera vez la sumatoria_Actual es 3 y el ultimo numero es el 3
# La tercera vez la sumatoria_Actual es 6 y el ultimo numero es el 4
print(f"Sumatoria con reduce {sumatoria}")
```
---

- ### max, min sorted

PAra numeros comunes
```python
import random

#Crear una lista de 100 numero al azar 
azar = [random.randint(1,100) for _ in range(1,101)]
#azar = {random.randint(1,100) for _ in range(1,101)}  #Si quisiera que no se repitan reemplazo los [] por {} para tener un set
print(azar)

maximo = max(azar)
print(f"El maximo es {maximo}")

minimo = min(azar)
print(f"El minimo es {minimo}")

ordenada = sorted(azar)
print(f"La lista ordenada es {ordenada}")
```

PAra diccionario
```python
personas = [
     {"nombre": "Esteban", "edad" : 45},
     {"nombre": "Juan", "edad" : 35},
     {"nombre": "maria", "edad" : 15},
]

personas_ordenadas = sorted(personas, key=lambda persona: persona["edad"])
print(personas_ordenadas)
```

# Generadores 

Los iterables que no ocupan memoria. Es un tipo especial de interable que produce los elementos bajo de demanda (lazy) en lugar de almacenar la coleccion em memoira
* Son eficientes en el uso de memoria
* Permiten trabajar con secuencias inffinitas
* El valor se calcula solamente cuando se pide

Vienen en dos sabores
* Manuales hechos por nosotros
* Creados por expresions generadoras (igual a las compresiones de listas)

> OJO: El parentesis se usa tanto para tuplas como para generadores

## Expresiones Generadoras

```python
#Expresiones Generadoras

#Quiero una lista con los numeros pares del 1 al 1_000 (o un millorn)
lista = [elem for elem in range(1,1001) if elem % 2 == 0]                #Este ocupa mucha memoria
generador_lazy = (elem for elem in range(1,1001) if elem % 2 == 0)      #Este no ocupa casi memoria, se calcula el valor cuando se pide

print(f"La lista ocupa {lista.__sizeof__()} bytes")
print(f"El generador ocupa {generador_lazy.__sizeof__()} bytes")

#Muestro la lista dos veces
print(f"Primera vez que muestro la lista {lista}")
print(f"Segunda vez que muestro la lista {lista}")

#Muestro el generador dos veces
print(f"\nTipo del Generador {type(generador_lazy)}")
print(f"Primera vez que muestro el generador {list(generador_lazy)}")
print(f"Segunda vez que muestro el generador {list(generador_lazy)}")
```

## Generdores Custom

```python
#Generador
def contador(max:int):
    i = 0
    while i < max:
      yield i  #Similar al return, pero la proxima vez que se ejecuta la funcion (con next sigue desde aca)
      i += 1

gen = contador(2)
print(gen)
print(next(gen)) # El next ejecuta el generador
print(next(gen))
print(next(gen)) #Si te pasa tira una excepcion de tipo StopIteration          
```

Todos los generadores son Iterables:

```python
#Generador
def contador(max:int):
    i = 0
    while i < max:
      yield i  #Similar al return, pero la proxima vez que se ejecuta la funcion (con next sigue desde aca)
      i += 1

gen = contador(10)
for elem in gen:
  print(elem)
```

# Expresiones Regulares

Son unas cadenas especiales que se utilizan para buscar patrones en un texto y para validar cadenas

- ## Expresiones regulares para validar entradas

```python
import re

#Validar que un texto tenga la forma AAAA-MM-DD
# ^ matchea con el inicio del texto
# $ matche con el fin del text0
patron = r"^[0-9]{4}-[0-9]{2}-[0-9]{2}$"
texto = input("Ingrese un texto que se va a validar con la expresion regular")

if re.match(patron, texto):
  print("El texto es valido")
else:
  print("El texto no es valido")
```

Otros ejemplos con Expresiones Regulares
```python
import re

texto = "Hola mi mail es esteban@gmail.com y mi telefono es 123-456-7890"

email = re.search(r"\w+@\w+\.\w+", texto)
print(email.group())

numeros = re.findall(r"[0-9]+", texto)
print(numeros)

nuevo_texto = re.sub(r"[0-9]+", "NUMEROS", texto)
print(nuevo_texto)
```
