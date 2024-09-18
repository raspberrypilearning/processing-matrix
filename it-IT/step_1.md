Quando usi le funzioni `rotate()` e `translate()` puoi salvare le impostazioni delle coordinate usando la funzione `push_matrix()` e, in seguito, ripristinarle usando la funzione `pop_matrix()`.

In questo esempio, per creare due occhi che si muovono, le impostazioni vengono salvate prima che venga disegnato uno dei due occhi. Lo schermo viene spostato e rotato prima che il primo occhio venga disegnato, poi le impostazioni vengono ripristinate prima che il secondo occhio venga disegnato.

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

