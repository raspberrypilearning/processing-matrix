Als je de functies `rotate()` en `translate()` gebruikt, kunt je de coördinaatinstellingen opslaan met de functie `push_matrix()` en vervolgens die coördinaatinstellingen herstellen met de functie `pop_matrix()`.

Om in dit voorbeeld twee roterende ogen te maken, worden de instellingen opgeslagen voordat een van de ogen wordt getekend. Het scherm wordt verschoven (translate) en gedraaid (rotate) voordat het eerste oog wordt getekend, waarna de instellingen worden hersteld voordat het tweede oog wordt getekend.

--- code ---
---
language: python
---

def oog():

# Maak een oog
  fill(WIT) 
  ellipse(0, 0, 150, 150) # Buitenkant oog 
  no_stroke() 
  fill(BLAUW) 
  ellipse(0, 0, 80, 80) # Iris 
  fill(ZWART) 
  ellipse(0, 0, 35, 35) # Pupil 
  fill(WIT, 70) 
  ellipse(-25, -20, 30, 30) # Lichtinval 1 met doorzichtigheid 
  ellipse(25, 25, 10, 10) # Lichtinval 2 met doorzichtigheid

def draw():

  global BLAUW, ZWART, WIT

  BLAUW = color(1, 32, 100)
  ZWART = color(0, 0, 0)
  WIT = color(255, 255, 255)

  background(WIT)
  translate(width/2, height/2) # Scherm naar het midden verplaatsen

  stroke(ZWART)
  ellipse(0, 0, 300, 300) # Hoofd

  push_matrix() # Slaat huidige scherminstellingen op

  translate(-100, 0) # Verplaats het scherm naar links voor het linkeroog
  for i in range(frame_count):
    oog()
    rotate(radians(45))

  pop_matrix() # Herstel vorige scherminstellingen (verwijdert de locatie en draaiing van het oog)

  translate(100, 0) # Verplaats het scherm naar rechts voor het rechteroog
  for i in range(frame_count):
    oog()
    rotate(radians(45))

--- /code ---
