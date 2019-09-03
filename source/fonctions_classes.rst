============================
Les fonctions et les classes
============================


Maintenant que vous avez vu comment créer une fonction de base, je vous propose d'en savoir un peu plus sur les fonctions. Puis nous aborderons les classes, des sortes de 'types' custom.


Création de fonctions plus complexes
====================================

Ce chapitre reprend basiquement la documentation officielle sur la `définition des fonctions <https://docs.python.org/fr/3/tutorial/controlflow.html#more-on-defining-functions>`_, donc si vous voulez lire une autre source, cliquez sur le lien. Sinon, bah restez ici.


------------------------------
Nommer les arguments à l'appel
------------------------------

Lorsque vous appelez une fonction, vous pouvez si vous le souhaitez préciser pour quel argument vous donnez une valeur. En partant de ce principe, il est possible de donner les arguments dans le désordre.

Par exemple avec la fonction définie comme suit : ``def foo(taille:int, nom:str, couleurs:list)``, vous pouvez l'appeler de plusieurs manières différentes : ``nom(3,'voiture', ['bleu','vert'])``, mais aussi ``nom(taille=3, nom='voiture', couleurs=['bleu','vert'])``, ou pourquoi pas ``nom(nom='voiture', couleurs=['bleu','vert'], taille=3)``.   
Il est aussi possible de mélanger les deux méthodes, dans ce cas les arguments sans noms doivent bien être placés dans l'ordre : ``nom(3, couleurs=['bleu','vert'], nom='voiture')``.

Cette technique est particulièrement utile lorsque la fonction accepte des arguments optionnels, comme nous allons le voir dès maintenant.


-------------------------------
Création d'arguments optionnels
-------------------------------

Il est possible de créer une fonction ayant des arguments que l'appel n'est *pas obligé* de fournir, ils sont donc optionnels. Par exemple dans la fonction ``route(stop:int,start:int=0)``, l'argument stop est obligatoire, mais l'argument start est optionnel : s'il n'est pas fourni, il prendra la valeur ``0``. Si vous n'en voyez pas l'utilité, attendez un peu de gagner de l'expérience, vous comprendrez vite.


-------------------
Arguments indéfinis
-------------------

Si vous ne savez pas par avance quels arguments vont être fournis, vous pouvez utiliser le symbole spécial ``*`` devant le nom de l'argument. Cet argument sera alors la liste de tous les arguments donnés à l'appel.

Regardez cet exemple pour mieux comprendre :

.. code-block:: py

    >>> def foo(n:int,*args):
    ...    print("n est de valeur",n)
    ...    print("J'ai aussi reçu comme arguments",args)
    
    >>> foo(3,8,4,'pizza')
    n est de valeur 3
    J'ai aussi reçu comme arguments [8,4,'pizza']

Encore mieux, il est possible de faire une liste indéfinie d'arguments *nommés*, avec une double astérisque. L'argument sera alors un dictionnaire (:py:class:`dict`) ayant pour clés les noms des arguments, et pour valeurs les arguments eux-même.

.. code-block:: py

    >>> def foo(n:int,**kwargs):
    ...    print("n est de valeur",n)
    ...    print("J'ai aussi reçu comme arguments",kwargs)
    
    >>> foo(3,parts=8,personnes=4,item='pizza')
    n est de valeur 3
    J'ai aussi reçu comme arguments {'parts': 8, 'personnes': 4, 'item': 'pizza'}


-----------------------------------------
Forcer l'utilisation des arguments nommés
-----------------------------------------

Dans certains cas particuliers, il est possible que le développeur force les arguments d'une fonction à être nommés explicitement. Dans ce cas il doit utiliser l'argument spécial ``*``, mais tout seul, pas devant le nom d'un argument.

Exemple :

.. code-block:: py

    def foo(n,*,parts,item):
        print("n est de valeur",n)
        print("Vous avez commandé 1",item,"avec",parts,"parts")

Si cette fonction est appelée avec un seul argument, Python va se plaindre qu'il manque des arguments, et c'est logique. Mais la fourberie est que si vous vous contentez de donner trois arguments, comme par exemple ``3,8,'pizza'``, vous vous trouverez face à une erreur :py:error:`TypeError` : "TypeError: foo() takes 1 positional argument but 3 were given". En effet la fonction ne demande qu'un seul argument positionnel alors que vous lui en donnez 3.

La seule et unique manière d'appeler cette fonction est donc ``foo(3,parts=8,item='pizza')``.
