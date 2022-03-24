Lorsque tu utilises les fonctions `rotate()` et `translate()`, tu peux enregistrer les paramètres de coordonnées à l'aide de la fonction `push_matrix()` , puis restaurer ces paramètres de coordonnées à l'aide de la fonction `pop_matrix()`.

Dans cet exemple, pour créer deux yeux rotatifs, les paramètres sont enregistrés avant que l'un ou l'autre des yeux ne soit dessiné. L'écran est translaté et pivoté avant que le premier œil ne soit dessiné puis les paramètres restaurés avant que le deuxième œil ne soit dessiné.

--- code ---
---
language: python

---

def œil():

# Créer un œil
  fill(BLANC)
  ellipse(0, 0, 150, 150) # Oeil extérieur
  no_stroke()
  fill(BLEU)
  ellipse(0, 0, 80, 80) # Iris
  fill(NOIR)
  ellipse(0, 0, 35, 35) # Pupille
  fill(BLANC, 70)
  ellipse(-25, -20, 30, 30) # Reflet spéculaire 1 avec opacité
  ellipse(25, 25, 10, 10) # Reflet spéculaire 2 avec opacité

def draw():

  global BLEU, NOIR, BLANC

  BLEU = color(1, 32, 100)
  NOIR = color(0, 0, 0)
  BLANC = color(255, 255, 255)

  background(BLANC)
  translate(width/2, height/2) # Déplacer l'écran vers le milieu

  stroke(NOIR)
  ellipse(0, 0, 300, 300) # Tête

  push_matrix() # Enregistre les paramètres d'écran actuels

  translate(-100, 0) # Déplacer l'écran vers la gauche pour l'œil gauche
  for i in range(frame_count):
    œil()
    rotate(radians(45))

  pop_matrix() # Restaure les paramètres d'écran précédents (supprime la translation et la rotation des yeux)

  translate(100, 0) # Déplacer l'écran vers la droite pour l'œil droit
  for i in range(frame_count):
    œil()
    rotate(radians(45))

--- /code ---