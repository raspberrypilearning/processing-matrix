Lorsque tu utilises les fonctions `rotate()` et `translate()` , tu peux enregistrer les paramètres de coordonnées à l'aide de la fonction `push_matrix()` , puis restaurer ces paramètres de coordonnées à l'aide de la fonction `pop_matrix()`.

Dans cet exemple, pour créer deux yeux rotatifs, les paramètres sont enregistrés avant que l'un ou l'autre des yeux ne soit dessiné. L'écran est translaté et pivoté avant que le premier œil ne soit dessiné puis les paramètres restaurés avant que le deuxième œil ne soit dessiné.

--- code ---
---
language: python

---

def eye(): # Create an eye fill(WHITE) ellipse(0, 0, 150, 150) # Outer eye no_stroke() fill(BLUE) ellipse(0, 0, 80, 80) # Iris fill(BLACK) ellipse(0, 0, 35, 35) # Pupil fill(WHITE, 70) ellipse(-25, -20, 30, 30) # Catchlight 1 with opacity ellipse(25, 25, 10, 10) # Catchlight 2 with opacity

def draw(): global BLUE, BLACK, WHITE

    BLUE = color(1, 32, 100)
    BLACK = color(0, 0, 0)
    WHITE = color(255, 255, 255)
    
    background(WHITE)
    translate(width/2, height/2) # Move screen to the middle
    
    stroke(BLACK)
    ellipse(0, 0, 300, 300) # Head
    
    push_matrix() # Saves current screen settings
    
    translate(-100, 0) # Move screen to the left for left eye
    for i in range(frame_count):
        eye()
        rotate(radians(45))
    
    pop_matrix() # Restores previous screen settings (removes the eye translation and rotation)
    
    translate(100, 0) # Move screen to the right for right eye
    for i in range(frame_count):
        eye()
        rotate(radians(45))

--- /code ---

