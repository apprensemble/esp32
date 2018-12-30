# esp32
Quelques exemple d'utilisation esp32 - NB : le BPI:BIT est à base d'un mcu ESP32

## environement
https://docs.espressif.com/projects/esp-idf/en/latest/get-started/linux-setup.html
### spec BPI:BIT
http://wiki.banana-pi.org/BPI-Bit

## micropython
https://github.com/micropython/micropython
http://docs.micropython.org/en/latest/library/machine.Pin.html

### Il suffit de suivre la doc micropython sur github
```
git clone git@github.com:micropython/micropython.git
cd micropython
git submodule update --init
cd ports/esp32
make deplibs
make
make erase
make deploy
# on lance le repl
screen /dev/ttyUSB0 115200
```

#### NB
Vous aurez certainement un message concernant la version du hash git de l'esp-idf (build chain)
il faudra aller dans votre rep esp-idf et faire : 
```
git checkout numero_de_hash
git submodule update
cd - # pour retourner dans le rep du ports/esp32 de micropython
#ensuite on rebuild
make clean
make deplibs
make
make erase
make deploy
# et on lance screen pour afficher le repl
```

### Ce que j'ai testé sur le bpi:bit avec un firmware contruit depuis les sources et non celui fourni par bpi:bit
Allumer/eteindre une led :
```python
from machine import Pin
Pin(18, Pin.OUT).value(1)
Pin(18, Pin.OUT).value(0)

# allumer la matrice de led en croix :
from neopixel import NeoPixel
Pin(2, Pin.OUT).value(1) #pour alimenter la matrice de led
np = NeoPixel(Pin(4), 25, bpp=3)
np[24] = (1, 0, 0)
np.write()
np[0] = (1, 0, 0)
np.write()
np[4] = (1, 0, 0)
np[20] = (1, 0, 0)
np.write()
np[12] = (1, 1, 0)
np.write()

# deplacement pixel avec les boutons
#afin d'obtenir les bonnes indentations faire ctrl+E avant de coller dans le repl puis ctrl+D apres avoir coller
from machine import Pin
from neopixel import NeoPixel
B = Pin(27, Pin.IN)
A = Pin(35, Pin.IN)
Pin(2, Pin.OUT).value(1) #pour alimenter la matrice de led
np = NeoPixel(Pin(4), 25, bpp=3)
x = 24
np[x] = (1, 0, 0)
np.write()
def avance(p):
  global x
  np[x] = (0, 0, 0)
  if x == 4:
    x = 20
  elif (x - 5) < 0:
    x = x + 21
  else:
    x = x - 5
  np[x] = (1, 0, 0)
  np.write()
def recule(p):
  global x
  np[x] = (0, 0, 0)
  if x == 20:
    x = 4
  elif (x + 5) > 24:
    x = x - 21 
  else:
    x = x + 5
  np[x] = (1, 0, 0)
  np.write()
B.irq(trigger=Pin.IRQ_FALLING, handler=avance)
A.irq(trigger=Pin.IRQ_FALLING, handler=recule)
```
Meme si les exemples concernent l'esp8266 ils fonctionnent également sur l'esp32 :
http://docs.micropython.org/en/latest/esp8266/quickref.html#neopixel-driver


Serait-il possible d'essayer de reproduire un effet de flames sur le BPI:BIT en microPhyton ?
Peut-être en s'inspirant d'un code arduino que j'ai trouvé :
https://github.com/giladaya/arduino-led-matrix/blob/master/fire/fire.ino

ou

https://github.com/darrenpmeyer/Arduino-FireBoard/blob/master/FireBoard.ino

par exemple...
