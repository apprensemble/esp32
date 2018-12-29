Installation mruby
==================

Recette d'installation mruby sur esp32

References
----------

* project original : `mruby`_.
* projet pour esp32 : `mruby-esp32`_.
  

Compilation
===========

J'ai pu compiler la dernière version de mruby en suivant exactement la même procedure qu'indiquée.
mruby-esp32 a preparée pour mruby 1.4.1 je l'ai fait fonctionner sans problème avec mruby 2.0.0.

**Avant compilation S'assurer que `esp-idf`_ est bien installer et dans le path**

.. code-block:: shell

    # pour l'exemple j'ai choisi le repl mruby : mirb
    git clone --recursive https://github.com/mruby-esp32/mruby-esp32-app-mirb.git
    # aller dans le dossier du projet original mirb:
    cd mruby-esp32-app-mirb/components/mruby/mruby
    # pointer vers la dernière version
    git checkout master
    # retourner à la racine mirb
    cd ../../..
    # selectionner le port serie auquel est relié votre esp32
    make menuconfig
    # compiler
    make
    # flasher et se connecter à la console
    make flash monitor
    
Si cela fonctionne vous devriez voir un prompt :

.. code-block:: ruby

    # faire un calcul
    1+1
    
Si cela fonctionne vous pouvez ensuite ajouter des fonctionnalités tel que la gestion des ports `gpio`_, la `memoire`_, le `wifi`_, l'`i2c`_ etc...





.. _mruby: https://github.com/mruby/mruby
.. _mruby-esp32: https://github.com/mruby-esp32
.. _gpio: https://github.com/mruby-esp32/mruby-esp32-gpio
.. _memoire: https://github.com/mruby-esp32/mruby-esp32-system
.. _wifi: https://github.com/mruby-esp32/mruby-esp32-wifi
.. _i2c: https://github.com/mruby-esp32/mruby-esp32-i2c
.. _esp-idf: https://docs.espressif.com/projects/esp-idf/en/latest/get-started/index.html
