عند استخدام `rotate()` و `translate()`، يمكنك حفظ إعدادات الإحداثيات باستخدام وظيفة `push_matrix()` ثم استعادة إعدادات الإحداثي هذه باستخدام وظيفة `pop_matrix()`.

في هذا المثال، لإنشاء عينين دائرتين، يتم حفظ الإعدادات قبل رسم أي من العينين. تتم ترجمة الشاشة وتدويرها قبل رسم العين الأولى ثم استعادة الإعدادات قبل رسم العين الثانية.

--- code ---
---
language: python

---

def eye():

# اصنع عين
  fill(WHITE)
  ellipse(0, 0, 150, 150) # العين الخارجية
  no_stroke()
  fill(BLUE)
  ellipse(0, 0, 80, 80) # قزحية
  fill(BLACK)
  ellipse(0, 0, 35, 35) # طالب
  fill(WHITE, 70)
  ellipse(-25, -20, 30, 30) # Catchlight 1 مع عتامه
  ellipse(25, 25, 10, 10) # Catchlight 2 مع عتامه

def draw():

  global BLUE, BLACK, WHITE

  BLUE = color(1, 32, 100)
  BLACK = color(0, 0, 0)
  WHITE = color(255, 255, 255)

  background(WHITE)
  translate(width/2, height/2) # حرك الشاشة الى المنتصف

  stroke(BLACK)
  ellipse(0, 0, 300, 300) # الراس

  push_matrix() # حفظ اعدادات الشاشة الحالية

  translate(-100, 0) # حرك الشاشة إلى اليسار للعين اليسرى
  for i in range(frame_count):
    eye()
    rotate(radians(45))

  pop_matrix() # استعادة إعدادات الشاشة السابقة (ازالة ترجمة العين والدوران)

  translate(100, 0) # حرك الشاشة إلى اليمين للعين اليمنى
  for i in range(frame_count):
    eye()
    rotate(radians(45))

--- /code ---

