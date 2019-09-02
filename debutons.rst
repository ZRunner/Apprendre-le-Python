Débutons le Python
==================

----------------------
Installation de Python
----------------------

Le plus simple est évidemment de l'installer depuis le site web officiel, cf. https://www.python.org/downloads. Néanmoins cela le rendra plus compliqué à mettre à jour, c'est pourquoi si vous connaissez un peu le terminal (ou 'console' sur Windows), il est préférable de l'installer depuis celui-ci.

Pour MacOS
----------

Personnellement, je vous conseille de passer par le célèbre programme 'brew', qui permet d'installer et de mettre à jour des 'paquets' (programmes, applications etc) très facilement sur Mac. Vous trouverez son installation via leur site web, https://brew.sh/index_fr.

Une fois brew installé, il suffit de rentrer dans le terminal ``brew install python``, et le téléchargement de la dernière version de Python 3 devrait se faire (à l'heure où j'écris ces lignes, il s'agit de Python 3.7.4).  
Pour la suite, un simple ``brew upgrade python`` permettra de maintenir Python à jour sur votre Mac.

Pour Linux
----------

Je ne connais pas le détail de toutes les distributions Linux, mais pour les environnements Unix/Debian par exemple, il existe la commande ``apt install`` (ou parfois ``apt-get install``) qui permet d'installer un paquet, comme le fait brew sur Mac. Cette commande est native au système, vous ne devriez pas avoir à la télécharger.

La commande pour installer python sera donc ``apt install python3``, qui vous installera la version de Python ayant été certifiée pour votre OS. Attention, elle n'est généralement pas la dernière version de Python, et peut donc présenter des incompatibilités avec ce guide. Pour installer une version précise, il faudra donc la télécharger et l'installer soi-même depuis le serveur officiel, comme suit : (n'oubliez pas de changer les numéros de version si besoin)

.. code-block:: bash

  wget https://www.python.org/ftp/python/3.7.4/Python-3.7.4.tgz
  tar xvf Python-3.7.3.tgz
  cd Python-3.7.4
  ./configure --enable-optimizations --enable-shared
  make -j8
  sudo make altinstall


Pour Windows
------------

Je ne connais pas la procédure d'installation spécifique à Windows, mais je sais par expérience qu'elle peut être assez douloureuse. Je conseille donc d'utiliser le téléchargement depuis le site officiel, c'est la méthode la plus sûre pour le moment.


----------------------------
Lancer l'interpréteur Python
----------------------------

Il est possible de lancer Python depuis votre terminal, et ce très simplement : entrez uniquement la commande ``python``. Notez que parfois cette commande peut ouvrir la version 2.7 de Python, auquel cas il faut utiliser la commande ``python3`` à la place.  
Vous obtiendrez alors quelque chose de semblable à ce qui suit : 

.. code-block::
  
  $ python3
  Python 3.7.4 (default, Jul  9 2019, 18:13:23)
  [Clang 10.0.1 (clang-1001.0.46.4)] on darwin
  Type "help", "copyright", "credits" or "license" for more information.
  >>>

Les trois chevrons ('>>>') indiquent que le programme attend de vous une instruction à exécuter. Vous pouvez alors écrire votre toute première instruction Python, par exemple ``print("Hello world")``, qui écrira dans le terminal la fameuse phrase 'Hello world'. Du même coup vous découvrez la *fonction* ``print``, qui permet d'afficher du texte ou d'autres choses dans le terminal. Nous reviendrons sur les chaînes de caractères (ou 'string') plus tard.

Pour quitter ce mode, vous devrez utiliser la fonction ``exit()``.


-------------------------------------
Quelques notes sur la commande python
-------------------------------------

La commande ``python`` ne vous permet pas seulement de lancer l'IDE, mais aussi de lancer un fichier écrit en Python (nous verrons cela plus tard), d'installer un paquet spécifique, de connaître la version installée de Python, etc.  
Quelques exemples : 

- ``python -V`` vous donnera la version utilisée par la commande
- ``python start.py`` lancera le ficher nommé 'start.py' installé dans le répertoire courant
- ``python ~/tests/start.py`` lancera le fichier 'start.py' installé dans le dossier 'tests' de votre répertoire utilisateur
- ``python -m pip install aiohttp`` installe la bibliothèque 'aiohttp', que vous pourrez utiliser dans votre code. Notez qu'il existe généralement l'alias `pip` pour vous éviter de taper `python -m`
