# Clase Tres - 08 de Octubre del 22025

## Repaso

* None - Especial
* NotImplemented - Especial
* list - Listas - []
    * Operadores : y ::
    * Metodos : pop()
* tuple - Tublas - ()
* set - Conjuntos - {}
    * Operadores : & | ^
* range - Rangos
* dict - Diccionarios - {}
* Tipo de Datos definidos por el usuario : Clases

Estructuras de control
* for
* if

---
---

## Genelidades de python

- ### Obtener un numero al azar
```python
#Quiero un numero entero al azar entre 1 y 100
import random

numero = random.randint(1,100)
print(numero)
```
---
- ### Expresiones condicionales / operadores ternarios
```python
mensaje = "par" if numero % 2 == 0 else "impar"  #En C o JAca o C# seria (numero % 2 == 0) ? "Par" : "Impar"
print(f"El número {numero} es {mensaje}.")
```
---
- ### Separar un string en una lista de caracteres
```python
#Yapa, nada que ver con funciones
cadena = "Hola que tal como andan"
lista = list(cadena)
print(lista)
```
---
- ### Tipo Not Implemented
Python tiene un tipo de dato llamado NotImplemented
---
- ### La libreria math tiene un valor especial nan (not a number)

Como en javascript!

```python
import math

print(f"La libreria math tiene un valor especial llamado nan {math.nan} que es de tipo  {type(math.nan)} ")
```
---

## Conversiones de tipo

* De range a list => list(range)
* De list a set => set(lista)   -> Es una buena manera facil de eliminar duplicados en una lista...
* De string a list => list(cadena)  -> Separa caracter por caracter

---
---

## Compresiones de Listas

Crear nuevas secuencias a partir de iterables (lista, tupla, rango, archivo) utilizando una sintaxis particular

> [expresion for elemento in iterable (if condicion)]
o bien explicito con operadores ternarios..
> [ valor if condicion else valor_alternativo for elemento in iterable (if condicion)]

* Recorremos la lista (elemento in iterable) a cada elemento le aplicamos la (expresion) nos quedamos con el elemento si aplica la condicion ((if condicion)

---
- ### Ejemplo sin if condicion
```python
lista = list(range(1,11))
print(lista)

#Lista cuadrados quiero que me hagan los cuadrados de la numeros [1,2,9,16...]
cuadrados = []

#Con un for tradicional
for el in lista:
  cuadrados.append(el**2)
print(cuadrados)

#Con compresiones de lista
cuadrados2 = [el**2 for el in lista]
print(cuadrados2)
``` 

---
- ### Ejemplo con if condicion
```

#Quiero los pares entre 1 y 100.Sin convertir el rango en una lista quiero los pares
#Nota podia crearlos de una range(2,101,2)

#Forma Tradicional
pares = []
for i in range(1,101):
    if i % 2 == 0:
        pares.append(i)
print(f"Números pares del 1 al 100 (bucle for + if): {pares}")

#Copresiones de lista
pares_compresion = [x for x in range(1,101) if x % 2 == 0]
print(f"Números pares del 1 al 100 (compresiones de lista): {pares_compresion}")
print(type(pares_compresion))
```
---
- ### Ejemplo con if y expresion ternaria
```python
#Quiero una lista de 20 numeros al azar entre -100 y 100
import random

numeros = [random.randint(-100,100) for _ in range(20)]  #Cuando no uso la variable de la compresion de lista uso _
print(numeros)

#Quiero una lista nueva de 20 elementos donde me diga ["negativo", "positivo"] (aca el cero lo consideramos positivo)

#Forma tradicional
print("\nForma Traicional:")
etiquetas = []  
for numero in numeros:
    if numero >= 0: 
        etiquetas.append("positivo")
    else:
        etiquetas.append("negativo")
print("Números:", numeros)
print("Etiquetas con for tradicional:", etiquetas)

#Forma tradicional con operador ternario
print("\nForma Traicional con operador ternario:")
etiquetas = []  
for numero in numeros:
    etiquetas.append("positivo" if numero>=0 else "negativo" )
print("Números:", numeros)
print("Etiquetas con for tradicional operador ternario:", etiquetas)

#Compresion de lista (usando tambien operadores ternairios)
print("\nCon Compresion de listas")
negpos = ["negativo" if num < 0 else "positivo" for num in numeros]
print("Números:", numeros)
print("Etiquetas con compresion de lista:", etiquetas)

#Quiero lo mismo utilizando compresiones de lista pero eliminando los pares del resultado final (con un filtro)
print("\nCon Compresion de listas con filtros y operadores ternarios")
numeros_sin_pares = [num for num in numeros if num % 2 != 0]
negpos = ["negativo" if num < 0 else "positivo" for num in numeros if num % 2 != 0]
print("Números:", numeros_sin_pares)
print("Etiquetas con compresion de lista sin pares:", negpos)
```
---
- ### Compresion de Diccionareios
```python
#Quiero generar por compresion un dicionrio donde la clave sea un nombre de la lista y el valor sea la cantidad de letras
#Compresion de diccionarios...
nombres = ["Ana", "Alicia", "Esteban", "Koldo", "Francesc"]

nombre_cantidad_letras = {nombre: len(nombre) for nombre in nombres}  #Uso llave en vez de corchetes y genero un diccionaro
print(nombre_cantidad_letras)
```

## Iterable

---
---

## Funciones (y Metodos)

- ### Funciones sin valor de retorno (Procedimientos)

```python
def saludar():
  print("Hola mundo de los metodos")

saludar()

retorno = saludar() #Me devuelve None
print(retorno)
```

---

- ### Funciones que devuelven algo
- 
```python
def sumar(a,b):
  return a+b

resultado = sumar(1,2)
print(resultado)
```

---

- ###  Especificar el nombre de los parametros al invocar

```python
#Especificar el nombre del parametro el invocar (muy comun en python)

def presentar(nombre, apellido):
  print(f"Soy {nombre} {apellido}")

presentar(nombre="Juan", apellido="Perez")
presentar("Juan", "Perez")
presentar(apellido="Perez", nombre="Juan")
```

---

- ### Parametros por defecto

```python
def saludar(nombre="Invitado"):
  print(f"Hola {nombre}")

saludar("Juan")
saludar()
```

---

- ### Parametros variables (tupla)

```
#Parametros variables

def sumar(*args): #Le pongo un asterisco...
  print(f"La funcion sumar recibio {args} de tipo {type(args)}")
  resultado = 0
  for arg in args:
    resultado += arg
  return resultado

print(f"La suma del 1 al 10 es {sumar(1,2,3,4,5,6,7,8,9,10)} \n")

lista = list(range(1,11))
#print(sumar(lista)) #Tira error, la tengo que "desempaquetar" la lista
print(f'La suma de lista desempaquetada es {sumar(*lista)} \n') #Le pongo un * adelante para desempaquetarla

print(f'La suma del rango desempaquetada es {sumar(*range(1,11))} \n') #Le pongo un * adelante para desempaquetarla

dict = {1:1, 4:2, 3:3}
print(f'La suma del dict desempaquetada es {sumar(*dict)} (Toma solo las claves) \n') #Le pongo un * adelante para desempaquetarla
```

---

- ### Parametros Variables (diccionario)

```python
#PArametros variables dicionario (Tengo los nombres de los parametros como parametro)
def saludar(**args):
    print(f"\nLa funcion saludar recibio {args} de tipo {type(args)}")
    for key, value in args.items():
        print(f"{key}: {value}")

saludar(nombre="Juan", apellido="Perez")
saludar(nombre="Juan", apellido="Perez", edad=30)

diccionario = {"nombre": "Juan", "apellido": "Perez", "edad": 30}
saludar(**diccionario)
```

---

- ### Especificacion funciones aun no implementadas

```python
# Funciones que todavia no termine de implementar

def funcion_no_implementada():     #Devuelve None
  pass

def funcion_no_implementada_2():   #Para la ejecucion y da error
  raise NotImplementedError("Esta funcion no esta implementada")

def funcion_no_implementada_3():   #Devuelve un tipo especial que se llama NotImplemented
  return NotImplemented


resultado = funcion_no_implementada()
print(resultado)

try:
  resultado = funcion_no_implementada_2()
  print(resultado)
except:
  print("Esto tira un error")

resultado = funcion_no_implementada_3()
print(resultado)

n = NotImplemented
print(type(n))
```

---

- ### Devolver varios valores en una funcion

Ejemplo1
```python
# Esto fue una de la razones por la que gente enloquecio con python
# Devolver varios valores en una sola funcion

def operaciones(a,b):
  return (a+b, a-b, a*b, a/b)

def operaciones_sin_parentesis(a,b):  #Igual devuelve una tupla
  return a+b, a-b, a*b, a/b

suma, resta, multiplicacion, division = operaciones(10,5)
print(f"Suma: {suma}, Resta: {resta}, Multiplicacion: {multiplicacion}, Division: {division}")

suma, resta, multiplicacion, division = operaciones_sin_parentesis(10,5)
print(f"Suma: {suma}, Resta: {resta}, Multiplicacion: {multiplicacion}, Division: {division}")
```

Ejemplo2
```python
#Lo de devolver varios parametros se puede usar para devolver el resultado de la operacion 
import math

print(f"La libreria math tiene un valor especial llamado nan {math.nan} que es de tipo  {type(math.nan)} ")

def dividir(a,b):
  if b == 0:
    return (math.nan, False)
  return (a/b, True)

divisor_como_cadena = input("Ingrese el divisor")
divisor = int(divisor_como_cadena) #Siempre que se pueda
cociente, correcto = dividir(10,divisor)
if correcto:
  print(f"Cociente: {cociente}, Correcto: {correcto}")
else:
  print(f"No se puede hacer la divicion. Cociente: {cociente}, Correcto: {correcto}")
```

Aparementemente las funciones en python pueden devolver varios valores pero en realidad es que estan devolviendo una tupla que luedo desempaquetamos

---

## Aspectos avanzados de funciones y expresiones Lamda

## Metodos de colecciones : map, fiter, reduce, max, min

## Decoradores

