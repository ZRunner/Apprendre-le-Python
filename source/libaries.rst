=================
Les bibliothèques
=================


----------------
Principe général
----------------


Les bibliothèques sont très utiles lorsque vous souhaitez créer des choses plus poussées. En effet, au bout d'un certain temps vous vous rendrez compte que certaines tâches basiques sont utilisées dans plusieurs projets, alors il deviendra plus pratique de le mettre dans un fichier séparé pour le réutiliser n'importe où (car le copié-collé est une chose à éviter **à tout prix** lorsqu'on code, pour plein de raisons différentes).

A ce moment-là, vous pourriez penser à l'envoyer à un pote qui en aurait besoin. Et pourquoi pas même le mettre en ligne sur un forum de devs. Eh bien sans le savoir, vous venez de partager votre première bibliothèque, ou *library* dans son nom anglais.

Une bibliothèque consiste donc en un code réutilisable dans votre propre code, via un import, qui vous permet d'effectuer certaines tâches. Il en existe des milliers, si ce n'est des millions, pour des choses extrêmement diverses, certaines beaucoup plus connues que d'autres. Par exemple la lib `requests <http://fr.python-requests.org/en/latest/>`_ qui gère l'utilisation des APIs de site web, `re <https://docs.python.org/fr/3/library/re.html>`_ pour les expressions regex, `asyncio <https://docs.python.org/fr/3/library/asyncio.html>`_ pour les fonctions asynchrones, et j'en passe. Il existe d'ailleurs le programme `PyPI <https://pypi.org/>`_ qui permet à n'importe quel dev un peu sérieux d'y déposer sa bibliothèque, et à n'importe qui de l'installer sur son ordinateur en une seule ligne dans le terminal (actuellement 194 880 projets y sont recensés).

D'une manière générale, pour importer une bibliothèque dans votre programme il suffit de mettre ``import <nom de la lib>``. Vous pouvez aussi importer des sous-parties, voire uniquement quelques fonctions/classes, grâce à ``from <nom de la lib> import <sous-partie>``. Attention, avec la première solution, il faudra renseigner les fonctions avec ``<nom de la lib>.<nom de la fonction>``! Mais il existe un moyen de contourner cela, en faisant ``from <nom de la lib> import *``

Je vais donc vous présenter ici quelques bibliothèques qu'il me semble important de connaitre. Pour le reste, je vous conseille encore une fois de chercher par vous-même, vous trouverez aisément.



-----------------
Quelques exemples
-----------------


Random
------

La bibliothèque `random <https://docs.python.org/fr/3/library/random.html>`_ est utilisé très vite par les développeurs, car elle permet de générer très facilement un pseudo-aléatoire. Partant de là, il est possible avec cette lib de par exemple obtenir un entier entre deux bornes, tirer un élément aléatoire dans une liste, mélanger une liste, ou d'autres fonctions beaucoup plus complexes.

Voilà un peu de code pour vous mettre en situation :

.. code-block:: py

    >>> import random
    >>> random.random()
    0.8848466154970993
    >>> random.random()
    0.6474755124505903
    >>> random.randrange(-15,24,step=5)
    -5
    >>> from random import shuffle
    >>> mylist = [1,2,3,4,5]
    >>> shuffle(mylist)
    >>> mylist
    [5, 2, 4, 3, 1]
    >>> random.choice(mylist)
    4


Requests
--------

Cette bibliothèque fait partie, selon certains sondages, des 10 bibliothèques les plus utilisées par les développeurs Python (à côté de `NumPy <https://numpy.org/>`_ et autres). Elle est fondamentale pour tout ce qui touche au web, et particulièrement au côté client des `API <https://fr.wikipedia.org/wiki/Interface_de_programmation>`_), car elle permet de poster différentes requêtes, avec la gestion des en-têtes (headers) et autres détails, tout en étant d'une simplicité déconcertante à utiliser.

Par exemple pour envoyer une requête 'GET' à l'adresse `https://discordapp.com/api/gateway`, nous utiliserons le code suivant :

.. code-block:: 

    >>> import requests
    >>> answer = requests.get('https://discordapp.com/api/gateway')
    >>> answer.ok
    True
    >>> answer.json()
    {'url': 'wss://gateway.discord.gg'}
    >>> answer.content # chaîne de caractères encodée en bits
    b'{"url": "wss://gateway.discord.gg"}'

Pour plus d'informations, n'hésitez pas à consulter `la documentation <http://fr.python-requests.org/en/latest/>`_, vous avez la chance d'en avoir une en français !


Regex
-----

Les `expressions régulières <https://fr.wikipedia.org/wiki/Expression_r%C3%A9guli%C3%A8re>`_, ou *regex* de son nom anglais est un concept assez difficile à appréhender pour un débutant, mais qui pourtant est utile dans bien des cas. Il s'agit d'"une chaîne de caractères, qui décrit, selon une syntaxe précise, un ensemble de chaînes de caractères possibles". C'est à dire que grâce à une chaîne de caractères précise, vous pourrez retrouver dans un texte toutes les occurences d'une recherche spécifique. Par exemple, récolter toutes les adresses http dans le code d'un site web, ou toutes les invitations Discord dans un message... les possibilités sont infinies ! 

.. note:: il existe deux version de cette lib, une incluse dans Python de base (``re``), l'autre à télécharger via la commande pip (``regex``). La deuxième est plus complète, mais pas forcément nécessaire pour une utilisation basique.

Il y a un site très connu pour aider à comprendre le fonctionnement du regex, et qui sert de zone de test : `regex101.com <https://regex101.com/>`_. Je vous laisse vous amuser dessus, tester les différentes syntaxes, les assembler pour voir ce qui fonctionne, bref, être curieux. En attendant, voici un exemple d'utilisation :

.. code-block:: py

    >>> import re
    >>> message1 = "Hey, rejoignez moi tous sur mon serveur http://discord.gg/minecraft !"
    >>> r = re.search(r'discord.gg/(\S+)',message1)
    >>> print("Ensemble :",r.group(0),"\nCode d'invitation :",r.group(1))
    Ensemble : discord.gg/minecraft 
    Code d'invitation : minecraft
    >>> # Un peu plus complexe maintenant...
    >>> message2 = """Je vous propose un premier site http://example.com\n Pourquoi pas même une version https, comme https://regex101.com ! Et que diriez-vous d'un www, par exemple https://www.google.fr/search?tbm=isch&q=python ?"""
    >>> for result in re.finditer(r'https?://(?:www\.)?(?P<domain>[^/\s]+)/?(?P<path>\S+)?',message2):
    ...    print("Domaine :",result.group('domain'),"- Chemin :",result.group('path'))
    Domaine : example.com - Chemin : None
    Domaine : regex101.com - Chemin : None
    Domaine : google.fr - Chemin : search?tbm=isch&q=python

Vous commencez à comprendre son utilisé maintenant ? 


