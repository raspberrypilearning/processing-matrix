Wrth ddefnyddio'r swyddogaethau `rotate()` a `translate()` fe allwch chi gadw'r gosodiadau cyfesurynnau drwy ddefnyddio'r swyddogaeth `push_matrix()`, ac yna adfer y gosodiadau hynny drwy ddefnyddio'r swyddogaeth `pop_matrix()`.

Yn yr enghraifft hon, i greu dwy lygad sy'n cylchdroi, mae'r gosodiadau'n cael eu cadw cyn llunio unrhyw lygad. Mae'r sgrin yn cael ei throsi a'i chylchdroi cyn llunio'r llygad gyntaf, yna mae'r gosodiadau'n cael eu hadfer cyn llunio'r ail lygad.

--- code ---
---
language: python
---

def llygad():

# Creu llygad
  fill(GWYN) 
  ellipse(0, 0, 150, 150) # Tu allan y llygad 
  no_stroke() 
  fill(GLAS) 
  ellipse(0, 0, 80, 80) # Iris 
  fill(DU) 
  ellipse(0, 0, 35, 35) # Cannwyll llygad 
  fill(GWYN, 70) 
  ellipse(-25, -20, 30, 30) # Goleubwynt 1 gydag afloywder 
  ellipse(25, 25, 10, 10) # Goleubwynt 2 gydag afloywder

def draw():

  global GLAS, DU, GWYN

  GLAS = color(1, 32, 100)
  DU = color(0, 0, 0)
  GWYN = color(255, 255, 255)

  background(GWYN)
  translate(width/2, height/2) # Symud y sgrin i'r canol

  stroke(DU)
  ellipse(0, 0, 300, 300) # Pen

  push_matrix() # Cadw'r gosodiadau sgrin presennol

  translate(-100, 0) # Symud y sgrin i'r chwith ar gyfer y llygad chwith
  for i in range(frame_count):
    llygad()
    rotate(radians(45))

  pop_matrix() # Adfer y gosodiadau sgrin blaenorol (tynnu trosiad a chylchdroad y llygad)

  translate(100, 0) # Symud y sgrin i'r dde ar gyfer y llygad dde
  for i in range(frame_count):
    llygad()
    rotate(radians(45))

--- /code ---

