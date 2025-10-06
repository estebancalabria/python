# Clase Uno - 06 de Octubre de 2025

## Python

* Requisitos para aprobar
  * Vamos un mini examen de 10 preguntas
  * Tener la asistencia
  * Seguir al profe en su instragram profesional : https://www.instagram.com/mct.esteban.calabria/

* Recursos
   * Wen Principal Python : https://www.python.org/ 

* Porque Python :
   * El lenguaje mas popular hoy por hoy : https://www.tiobe.com/tiobe-index/
   * Posee un ecosistema ENORME de librerias
   * Exploto con todo lo que es Inteligencia Artficial
   * Muy Versatil para cualquier tipo de aplicacion
   * Todos los caminos IT conducen a Python
     

### Usos de Python
* Inteligencia Artificial
* Data Science
* Automatizacion
    * Flujos Empresariales
    * Devops
    * Administracion Sistemas
    * Testing Automatizado
 * Tipos de Aplicaciones
    * Aplicaciones de Escritorio
    * Aplicaciones Web
    * Aplicaciones de Consola
    * Juegos
    * Aplicaciones de Datos (ML, DScience, etc)

### Caracteristicas de Python

* No es fuertemente tipado como Java
   * Si bien cada variable tiene un tipo de datos, pueder transparente para el usuario
* Permite tanto programacion estructurada como Orientada a Objetos
* Es un lenguaje Interpretado
* Los archivos de python tienen extension .py
* No usa ni punto (;) ni llaves ({}) el codigo debe estar correctamente identado

### Entornos de Desarrollo

* Visual Studio Code : https://code.visualstudio.com/
   * Extensiones Recomendadas:
      * Python
      * Github Copilot (IA)
* Notebooks online : https://colab.google/

### Primeros Pasos

Puedo Ejecutar mi Hola mundo desde:
* Directamente el interprete de python desde la linea de comando
* Creando un archivo hola-mundo.py y ejecutandolo como python hola-mundo.py desde la terminal
* Desde una celda de google colab

```python
print("Hola Mundo")
```

### Manejo de librerias

* El administrador de librerias de python se llama pip
* Vamos a verificar su instalacion ejecutando pip --version en la terminal

### Hola Mundo Juegos

Vamos a ChatGPT y le pedimos que nos genere un juego con pygame
Prompt:
```
Me podes generar el juego snake en python usando la libreria pygame
```

Genero
```python

import pygame
import random
import sys

# Inicializar Pygame
pygame.init()

# Configuración de pantalla
WIDTH, HEIGHT = 600, 400
CELL_SIZE = 20
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("🐍 Snake en Python")

# Colores
BLACK = (0, 0, 0)
GREEN = (0, 200, 0)
RED = (200, 0, 0)
WHITE = (255, 255, 255)

# Reloj
clock = pygame.time.Clock()
FPS = 10

# Fuente
font = pygame.font.SysFont("consolas", 25)

def draw_snake(snake):
    for x, y in snake:
        pygame.draw.rect(screen, GREEN, (x, y, CELL_SIZE, CELL_SIZE))

def draw_food(food):
    pygame.draw.rect(screen, RED, (food[0], food[1], CELL_SIZE, CELL_SIZE))

def show_score(score):
    score_text = font.render(f"Puntos: {score}", True, WHITE)
    screen.blit(score_text, [10, 10])

def main():
    # Posición inicial de la serpiente
    snake = [(100, 100), (80, 100), (60, 100)]
    direction = "RIGHT"

    # Posición inicial de la comida
    food = (
        random.randrange(0, WIDTH // CELL_SIZE) * CELL_SIZE,
        random.randrange(0, HEIGHT // CELL_SIZE) * CELL_SIZE
    )

    score = 0

    while True:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                sys.exit()

            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_UP and direction != "DOWN":
                    direction = "UP"
                elif event.key == pygame.K_DOWN and direction != "UP":
                    direction = "DOWN"
                elif event.key == pygame.K_LEFT and direction != "RIGHT":
                    direction = "LEFT"
                elif event.key == pygame.K_RIGHT and direction != "LEFT":
                    direction = "RIGHT"

        # Mover la serpiente
        x, y = snake[0]
        if direction == "UP":
            y -= CELL_SIZE
        elif direction == "DOWN":
            y += CELL_SIZE
        elif direction == "LEFT":
            x -= CELL_SIZE
        elif direction == "RIGHT":
            x += CELL_SIZE

        new_head = (x, y)
        snake.insert(0, new_head)

        # Comprobar si come la comida
        if new_head == food:
            score += 1
            food = (
                random.randrange(0, WIDTH // CELL_SIZE) * CELL_SIZE,
                random.randrange(0, HEIGHT // CELL_SIZE) * CELL_SIZE
            )
        else:
            snake.pop()

        # Colisiones
        if (
            x < 0 or x >= WIDTH or
            y < 0 or y >= HEIGHT or
            new_head in snake[1:]
        ):
            game_over_text = font.render("💀 GAME OVER 💀", True, RED)
            screen.blit(game_over_text, [WIDTH // 2 - 100, HEIGHT // 2 - 20])
            pygame.display.flip()
            pygame.time.wait(2000)
            main()

        # Dibujar
        screen.fill(BLACK)
        draw_food(food)
        draw_snake(snake)
        show_score(score)
        pygame.display.flip()

        clock.tick(FPS)

if __name__ == "__main__":
    main()

```

Si lo ejecuto me va tirar el error de que no tengo instalada la libreria pygame
```cmd
File "c:\....\02-juego-snake.py", line 1, in <module>
    import pygame
ModuleNotFoundError: No module named 'pygame'
```

> Cuando un programa de python arroja un error decimos que lanza una excepcion...

Voy a instalar la libreria pygame
```cmd
pip install pygame
```
    
Algunos usuarios tuvieron temas para instalar la libreria por un tema de permiros y lo resolvieron:
```cmd
pip install --user pygame
```

Para saber si se instalo bien
```cmd
python -m pygame.examples.aliens
```

