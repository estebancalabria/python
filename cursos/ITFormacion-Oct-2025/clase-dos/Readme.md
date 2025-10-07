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

- #### Operaciones (Slicing, step y pertenencia)

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
- 

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
