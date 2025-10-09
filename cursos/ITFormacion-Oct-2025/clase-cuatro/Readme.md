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
