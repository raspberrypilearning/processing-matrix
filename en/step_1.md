When using `rotate()` and `translate()` functions you can save the coordinate settings by using the `push_matrix()` function then restore those coordinate settings using the `pop_matrix()` function.

In this example, to create two rotating eyes, the settings are saved before either of the eyes are drawn. The screen is translated and rotated before the first eye is drawn then the settings restored before the second eye is drawn.

--- code ---
---
language: python

---

def eye():
    # Create an eye
    fill(WHITE)
    ellipse(0, 0, 150, 150) # Outer eye
    no_stroke()
    fill(BLUE)
    ellipse(0, 0, 80, 80) # Iris
    fill(BLACK)
    ellipse(0, 0, 35, 35) # Pupil
    fill(WHITE, 70)
    ellipse(-25, -20, 30, 30) # Catchlight 1 with opacity
    ellipse(25, 25, 10, 10) # Catchlight 2 with opacity

def draw():
    global BLUE, BLACK, WHITE
    
    BLUE = Color(1, 32, 100)
    BLACK = Color(0, 0, 0)
    WHITE = Color(255, 255, 255)
    
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

