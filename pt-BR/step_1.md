Ao usar as funções `rotate()` e `translate()`, você pode salvar as coordenadas definidas usando a função `push_matrix()` e recuperá-las usando a função `pop_matrix()`.

Neste exemplo, para criar dois olhos rotativos, as definições são salvas antes que qualquer um dos olhos seja desenhado. A tela é transladada e rotacionada antes que o primeiro olho seja desenhado e as definições são restauradas antes que o segundo olho seja desenhado.

--- code ---
---
language: python

---

def olho():
    # Cria um olho
    fill(BRANCO)
    ellipse(0, 0, 150, 150) # Circulo externo do olho
    no_stroke()
    fill(AZUL)
    ellipse(0, 0, 80, 80) # Íris
    fill(PRETO)
    ellipse(0, 0, 35, 35) # Pupila
    fill(BRANCO, 70)
    ellipse(-25, -20, 30, 30) # Brilhos nos olhos 1 com opacidade
    ellipse(25, 25, 10, 10) # Brilho nos olhos 2 com opacidade

def desenhar():
    global AZUL, PRETO, BRANCO

    AZUL = color(1, 32, 100)
    PRETO = color(0, 0, 0)
    BRANCO = color(255, 255, 255)
    
    background(BRANCO)
    translate(width/2, height/2) # Move a tela para o meio
    
    stroke(PRETO)
    ellipse(0, 0, 300, 300) # Cabeça
    
    push_matrix() # Salva as definições atuais da tela
    
    translate(-100, 0) # Move a tela para a esquerda, para desenhar o olho esquerdo
    for i in range(frame_count):
        olho()
        rotate(radians(45))
    
    pop_matrix() # Restaura as definições anteriores da tela (remove a translação e a rotação dos olhos)
    
    translate(100, 0) # Move a tela para a direita, para desenhar o olho direito
    for i in range(frame_count):
        olho()
        rotate(radians(45))

--- /code ---

