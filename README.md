# esp32
Quelques exemple d'utilisation esp32 - NB : le BPI:BIT est à base d'un mcu ESP32

## Qu'est-ce que l'esp32

L'esp32 est un microcontrolleur puissant très ouvert et ultrapopulaire.

## Specifications

https://docs.espressif.com/projects/esp-idf/en/latest/get-started/linux-setup.html

### spec BPI:BIT
http://wiki.banana-pi.org/BPI-Bit

### spec esp32 lolin avec ssd1306
**NB: sur ma carte le SDA est sur le pin 5 et le SCL sur le pin 4.**
C'est l'inverse de l'article suivant : https://projetsdiy.fr/deballage-clone-wemos-esp32-lolin-ecran-oled-monochrome-ssd1306/


## Objectifs

Donner une vue générale des possibilités offertes par l'esp32 et aider à commencer un projet dans le langage de son choix.
Chaque démarage dans un langage sera accompagné d'exemples documentés en français. Pour le moment j'ai commencé micropython et mruby. L'objectif est de couvrir tout les langages que je cite.

## Langages abordés :

### Partiellement disponible :

* [micropython](https://esp32-fr.readthedocs.io/fr/latest/micropython/micropython.html)
* [mruby](https://esp32-fr.readthedocs.io/fr/latest/mruby/mruby.html)

### Pas encore commencé :

* [freertos](https://docs.espressif.com/projects/esp-idf/en/latest/get-started/linux-setup.html)
* [arduino IDE](https://github.com/espressif/arduino-esp32)
* [tinyGo](https://github.com/aykevl/tinygo)
* ~~[HaikuVM](http://haiku-vm.sourceforge.net/)~~ ne fonctionne pas encore sur esp32
* [javascript](http://www.espruino.com/ESP32)
* [lua](https://nodemcu.readthedocs.io/en/dev-esp32/en/build/)
* ...


### Idées de projets (cassiope34) :

Serait-il possible d'essayer de reproduire un effet de flames sur le BPI:BIT en microPhyton ?
Peut-être en s'inspirant d'un code arduino que j'ai trouvé :
https://github.com/giladaya/arduino-led-matrix/blob/master/fire/fire.ino

ou

https://github.com/darrenpmeyer/Arduino-FireBoard/blob/master/FireBoard.ino
(exemple micropython : https://gist.github.com/aykevl/0b4031c95575a4674772216e4b0f3b64)

par exemple...

La librairie FastLED https://github.com/FastLED/FastLED/releases qui remplacerait avantageusement celle d'ADAFRUIT https://github.com/adafruit/Adafruit_NeoPixel  d'après un gars sur le site AdaFruit https://learn.adafruit.com/adafruit-neopixel-uberguide/advanced-coding
