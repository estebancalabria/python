# Clase Tres - 08 de Octubre del 22025

## Repaso

* None - Especial 
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

## Genelidad de python

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

## Conversiones de tipo

* De range a list => list(range)
* De list a set => set(lista)   -> Es una buena manera facil de eliminar duplicados en una lista...

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

## Metodos

## Expresiones Lambda

## Metodos de colecciones : map, fiter, reduce, max, min

## Decoradores

