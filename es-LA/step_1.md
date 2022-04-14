Al utilizar las funciones `rotate()` y `translate()`, puedes guardar la configuración de coordenadas utilizando la función `push_matrix()` y luego restaurar esa configuración de coordenadas utilizando la función `pop_matrix()`.

En el ejemplo a continuación, para crear dos ojos giratorios, la configuración se guarda antes de dibujar cualquiera de los ojos. La pantalla se traslada y gira antes de que se dibuje el primer ojo y luego se restablece la configuración antes de que se dibuje el segundo ojo.

--- code ---
---
language: python
---

def ojo():

# Crea un ojo
  fill(BLANCO)
  ellipse(0, 0, 150, 150) # Exterior del ojo
  no_stroke()
  fill(AZUL)
  ellipse(0, 0, 80, 80) # Iris
  fill(NEGRO)
  ellipse(0, 0, 35, 35) # Pupila
  fill(BLANCO, 70)
  ellipse(-25, -20, 30, 30) # Brillo ocular 1 con opacidad
  ellipse(25, 25, 10, 10) # Brillo ocular 2 con opacidad

def draw():

  global AZUL, NEGRO, BLANCO

  AZUL = color(1, 32, 100)
  NEGRO = color(0, 0, 0)
  BLANCO = color(255, 255, 255)

  background(BLANCO)
  translate(width/2, height/2) # Mueve la pantalla al centro

  stroke(NEGRO)
  ellipse(0, 0, 300, 300) # Cabeza

  push_matrix() # Guarda la configuración de pantalla actual

  translate(-100, 0) # Mueve la pantalla a la izquierda para el ojo izquierdo
  for i in range(frame_count):
    ojo()
    rotate(radians(45))

  pop_matrix() # Restaura la configuración de pantalla anterior (elimina la traslación y rotación de los ojos)

  translate(100, 0) # Mueve la pantalla a la derecha para el ojo derecho
  for i in range(frame_count):
    ojo()
    rotate(radians(45))

--- /code ---
