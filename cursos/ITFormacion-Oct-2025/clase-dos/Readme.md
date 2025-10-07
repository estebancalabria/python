# Clase Dos - 07 de Octubre del 2025

## Repaso

* Seguir el Instagram del Profe y Darle Like : https://www.instagram.com/p/C_VyOHHRv0N/?img_index=1
* Librerias
  * pip
  * pygame : https://www.pygame.org/
* Comentarios
* Tipos de Datos
    * int
    * float
    * bool
    * complex
    * string
        * inmutables
        * formateo de strings f'...'

## Recursos

* Estamos trabajando en Google Colab : https://colab.google/
* Si lo quiero ejecutar localmente : https://jupyter.org/

## Tipos de datos (estructurados)

* Listas        =>  []
* Tuplas        =>  ()
* Rangos        =>  range
* Enumerate     => enumetate
* Conjuntos     => {}
* Diccionarios  => {}

### listas

- #### Declaracion

```python
lista = [1,2,3,4,5]
listas_nombres = ["Juan", "Pedro", "Ana"]
lista_mixta = [1, "ana", 3.5]

print(type(lista))
print(len(lista))
print(type(lista[0]))
```

- #### Operaciones (Slicing, step y pertenencia)

```python
"""
En esta celda vamos a ver operaciones sobre  las listas mutables
"""

lista = [1,2,3,4,5,6,7,8,9,10]

# Operacioens Basica
print(f"La lista es {lista}")
print(f"La longitud de la lista es {len(lista)}")
print(f"El primer elemento de la lista ( lista[0] ) es { lista[0] }")
print(f"El ultimo elemento de la lista ( lista[-1] ) es {lista[-1]}")
print(f"Tambien...el ultimo elemento de la lista (lista[len(lista)-1]) es {lista[len(lista)-1]}")

# Slicing :
# Los primeros 5 elementos de la lista
print("\nSlicing (:)")
print(f"Los primeros 5 elementos de la lista : {lista[:5]}") #5 elemento
print(f"Los primeros 5 elementos de la lista : {lista[:-5]}") #Wow lo puse por error
print(f"Los primeros 5 elementos de la lista : {lista[0:5]}") 
# Caso especial 
print(f"Si hago (lista[1:1]) {lista[1:1]} veo que la posicion de fin no la incluye y me da []") 
print(f"Si hago (lista[4:2]) {lista[4:2]} veo que la posicion de fin no la incluye y me da []") 
print(f"Si hago (lista[4:2000]) me da {lista[4:2000]} (no tengo tantos problemas de overflow)") 
# Los ultimos 5 elementos de la lista
print(f"Los primeros 5 elementos de la lista : {lista[-5:]}")
# Del segundo al ante ultimo
print(f"Del segundo al anteúltimo: {lista[1:-1]}")  #Aca es posicion_inicio : posicion_fin (no incluye la posicion de fin)
print(f"Del segundo al anteúltimo: {lista[1:9]}")

# Operador de paso (step) ::  posicionInicial : PosicionFinal (una antes) : salto
# La lista invertida, en reversa
print("\nStep (::)")
print(f"La lista invertida (lista[::-1]) es  {lista[::-1]}")
# La lista invertida del ante penultimo al tercero
print(f"La lista invertida del ante penultimo al tercero (lista[-3:1:-1]) { lista[-3:1:-1] }")
# Los elementos de la lista en posiciones pares
print(f"Los elementos en posiciones pares{lista[1::2]}")

#Pertenencia
print("\nPertenencia:")
print(f"El 5 pertenece en la lista {5 in lista}")
print(f"El 15 pertenece en la lista {15 in lista}")
print(f"El 25 no pertenece en la lista {25 not in lista}")
```

- #### Concatenacion y repeticion

```python
lista1 = [1,2,3,4,5]
lista2 = [6,7,8,9,10]

if lista2 > lista1:            #Compara elemento a elemento, los valores
    print("lista2 es mayor")
elif lista1> lista2 :
    print("lista1 es mayor")

# Las listas se pueden concatenar como los string
lista_total = lista1 + lista2

# El operador de multiplicar
lista_de_ceros  = [0] * 10
print(lista_de_ceros)

#Recorrer la lista
for elemento in lista_total:
    print(elemento)
```

 - #### Metodos de la lista

```python
lista = [1,3,4,5]
print(lista)

print("\nAppend 6")
lista.append(6)
print(lista)

print("\nInsert 1,2")
lista.insert(1,2) #Inserta en la posicion 1 el 2 
print(lista)

print("\nExtendemos [7,8,9]")
lista.extend([7,8,9])
print(lista)

print("\nAgrego y luego Remove 9")
lista.append(45)
print(lista)
lista.remove(45)  #Saca el primero, si esta varias veces lo saca una sola vez
print(lista)

print("\nPop")  #Saca el ultimo
lista.pop()
print(lista)

lista.pop(0) #Saca el primero
print(lista)

print("\nReverse")
lista.reverse()
print(lista)

print("\nAgrego -1 y ordeno")
lista.append(-1)
print(lista)
lista.sort()
print(lista)
```

### Tuplas

```python
lista = [1,2,3]
tupla = (1,2,3)

print(lista)
print(tupla)

print(type(lista))
print(type(tupla))

try:
  tupla[1] = 3
except:
  print("No se puede modificar una tupla dio error")


#Desempaquetar
tupla = (1,2,3)
variable1, variable2, variable3 = tupla
print(variable1)
print(variable2)
print(variable3)

#Desempaquetar sirve tambien para las listas
lista = [1,2,3]
variable1, variable2, variable3 = lista
print(variable1)
print(variable2)
print(variable3)

#Esto da error si o si tengo que sacar todas
#variable1, variable2 = tupla
#print(variable1)
#print(variable2)

`` 

### Rangos

```python
lista = [1,2,3,4,5]
rango = range(1,6)   #El rango es como el :: el ultimo elemento no lo incluye
lista_de_rango = list(rango)

print(lista)
print(rango)
print(lista_de_rango)

print(type(lista))
print(type(rango))

#Es iterable
for elemento in range(1,10):
  print(elemento)

print(f"Rango especificando solo el casi ultimo {list(range(5))} ")  
print(f"Rango especificando el primero y el casi ultimo {list(range(1,5))} ")  
print(f"Rango especificando un salto (range(1,11,2)) {list(range(1,11,2))} ") 
print(f"Rango de atras para adelante (range(10,0,-1)) {list(range(10,0,-1))} ") 

lista = ["Juan", "Pedro", "Ana", "Laura"]
for nombre in lista:
  print(nombre)

for i in range(len(lista)):
  print(f"Posicion {i} elemento {lista[i]}")


#print(enumerate(lista))
for i, nombre in enumerate(lista):
  print(f"Posicion {i} elemento {nombre}")

# ["Juan", "Pedro", "Ana", "Laura"]  => enumetate(["Juan", "Pedro", "Ana", "Laura"]) => [(0,"Juan"), (1,"Pedro"), (2,"Ana"), (3,"Laura")]
```

### Conjuntos

Operadores
* in
* not in
* & (interseccion)
* | (union)
* - (diferencia)
* ^ (union menos intereseccion)
   
```python
# Es como una lista que no admite valores repetidos

nombre = {"Juan", "Pedro", "Ana", "Laura"}
print(nombre)
print(type(nombre))

nombre = {"Juan", "Pedro", "Ana", "Laura", "Juan"}  #Incluyo un elemento duplicado
print(nombre)

vacio = set() #Las llaves se usan tanto para conjuntos como para diccionario, entonces para conjuntos vacios usamos set
print(vacio)

print(type(set()))  #<class 'set'>
print(type({}))     #<class 'dict'>


#Operacione entre conjuntos
millonarios = {"Musk","Gates","MrBeast"}
inteligentes = {"Musk","Gates","Einstein"}

print("millonarios_inteigentes")
millonarios_inteigentes = millonarios & inteligentes        #interseccion
print(millonarios_inteigentes)

print("millonarios no inteligentes")
millonarios_no_inteligentes = millonarios - inteligentes    #Diferencia (al primer grupo le quito los del segudno)
print(millonarios_no_inteligentes)

print("o millonarios o inteligentes")
pobres_inteligentes = millonarios ^ inteligentes         #Diferencia simetrica (lo contrario a la interseccion)
print(pobres_inteligentes)

print("Union")
todos = millonarios | inteligentes                         #Union
print(todos)

#Podemos usar el in y el not inn
musk_es_inteligente = "Musk" in inteligentes
print(f"Musk es inteligente { musk_es_inteligente  }")

```

Metodos para conjuntos

```python
frutas = {"manzana", "platano"}
frutas.add("naranja")   #Agrego uno solo
frutas.update(["kiwi", "uva"])   #Agrego varios
frutas.discard("platano")  #Nuncca da un error
frutas.remove("kiwi") #Da error si no existe
frutas.pop() #Remueve un elemento aleatorio, conceptualmente los conjuntos no tienen un orden
print(frutas)

frutas.clear()
print(frutas)

```

## Estructuras de control

### IF 

```python
lista1 = [1,2,3,4,5]
lista2 = [6,7,8,9,10]

if lista2 > lista1:            #Compara elemento a elemento
    print("lista2 es mayor")
elif lista1> lista2 :
    print("lista1 es mayor")
```

### For

```python
for elemento in lista_total:
    print(elemento)
```

Opciones de FOR

```python
lista = ["Juan", "Pedro", "Ana", "Laura"]

#Recorro la lista
for nombre in lista:
  print(nombre)

#Recorro un rango
for elemento in range(1,10):
  print(elemento)

#Recorro un rango y una lista a la vez
for i in range(len(lista)):
  print(f"Posicion {i} elemento {lista[i]}")

#Recorro un enumerate
#print(enumerate(lista))
for i, nombre in enumerate(lista):
  print(f"Posicion {i} elemento {nombre}")
```
