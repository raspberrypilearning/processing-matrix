Quando usi le funzioni `rotate()` e `translate()` puoi salvare le impostazioni delle coordinate usando la funzione `push_matrix()` e, in seguito, ripristinarle usando la funzione `pop_matrix()`.

In questo esempio, per creare due occhi che si muovono, le impostazioni vengono salvate prima che venga disegnato uno dei due occhi. Lo schermo viene spostato e rotato prima che il primo occhio venga disegnato, poi le impostazioni vengono ripristinate prima che il secondo occhio venga disegnato.

--- code ---
---
language: python

---

def occhio():
    # Disegna un occhio
    fill(BIANCO)
    ellipse(0, 0, 150, 150) # Parte esterna dell'occhio
    no_stroke()
    fill(BLU)
    ellipse(0, 0, 80, 80) # Iride
    fill(NERO)
    ellipse(0, 0, 35, 35) # Pupilla
    fill(BIANCO, 70)
    ellipse(-25, -20, 30, 30) # Riflesso 1 con opacità
    ellipse(25, 25, 10, 10) # Riflesso 2 con opacità

def draw():
    global BLU, NERO, BIANCO
    
    BLU = color(1, 32, 100)
    NERO = color(0, 0, 0)
    BIANCO = color(255, 255, 255)
    
    background(BIANCO)
    translate(width/2, height/2) # Sposta lo schermo al centro
    
    stroke(NERO)
    ellipse(0, 0, 300, 300) # Testa
    
    push_matrix() # Salva le impostazioni attuali dello schermo
    
    translate(-100, 0) # Sposta lo schermo a sinistra per l'occhio sinistro
    for i in range(frame_count):
        occhio()
        rotate(radians(45))
    
    pop_matrix() # Ripristina le impostazioni dello schermo precedenti (rimuovi la traslazione e la rotazione dell'occhio)
    
    translate(100, 0) # Sposta lo schermo a destra per l'occhio destro
    for i in range(frame_count):
        occhio()
        rotate(radians(45))

--- /code ---

