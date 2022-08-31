`rotate()`および`translate()`関数を使用するときに、`push_matrix()`関数を使用して座標設定を保存し、`pop_matrix()`関数を使用して保存した座標設定を復元できます。

この例では、回転する2つの目を作成するために、片方の目を描画する前に設定を保存しています。 最初の目を描画する前に画面を平行移動および回転し、2番目の目を描画する前に設定を復元しています。

--- code ---
---
language: python

---

def eye():

# 目を作成する
  fill(WHITE)
  ellipse(0, 0, 150, 150) # 目の形
  no_stroke()
  fill(BLUE)
  ellipse(0, 0, 80, 80) # 虹彩
  fill(BLACK)
  ellipse(0, 0, 35, 35) # 瞳
  fill(WHITE, 70)
  ellipse(-25, -20, 30, 30) # 不透明度設定を使った光の当たり方の表現1
  ellipse(25, 25, 10, 10) # 不透明度設定を使った光の当たり方の表現2

def draw():

  global BLUE, BLACK, WHITE

  BLUE = color(1, 32, 100)
  BLACK = color(0, 0, 0)
  WHITE = color(255, 255, 255)

  background(WHITE)
  translate(width/2, height/2) # 画面を中央に移動する

  stroke(BLACK)
  ellipse(0, 0, 300, 300) # 頭

  push_matrix() # 現在の画面設定を保存する

  translate(-100, 0) # 左目を描くため画面を左に移動する
  for i in range(frame_count):
    eye()
    rotate(radians(45))

  pop_matrix() # 元の画面設定を復元する（目の描画のための平行移動と回転を取り消す）

  translate(100, 0) # 右目を描くため画面を右に移動する
  for i in range(frame_count):
    eye()
    rotate(radians(45))
--- /code ---
