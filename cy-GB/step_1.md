Wrth ddefnyddio'r swyddogaethau `rotate()` a `translate()` fe allwch chi gadw'r gosodiadau cyfesurynnau drwy ddefnyddio'r swyddogaeth `push_matrix()`, ac yna adfer y gosodiadau hynny drwy ddefnyddio'r swyddogaeth `pop_matrix()`.

Yn yr enghraifft hon, i greu dwy lygad sy'n cylchdroi, mae'r gosodiadau'n cael eu cadw cyn llunio unrhyw lygad. Mae'r sgrin yn cael ei throsi a'i chylchdroi cyn llunio'r llygad gyntaf, yna mae'r gosodiadau'n cael eu hadfer cyn llunio'r ail lygad.

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

