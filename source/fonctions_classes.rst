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

Si cette fonction est appelée avec un seul argument, Python va se plaindre qu'il manque des arguments, et c'est logique. Mais la fourberie est que si vous vous contentez de donner trois arguments, comme par exemple ``3,8,'pizza'``, vous vous trouverez face à une erreur :py:exc:`TypeError` : "TypeError: foo() takes 1 positional argument but 3 were given". En effet la fonction ne demande qu'un seul argument positionnel alors que vous lui en donnez 3.

La seule et unique manière d'appeler cette fonction est donc ``foo(3,parts=8,item='pizza')``.


--------------------------------------------------
Utiliser une liste/un dictionnaire comme arguments
--------------------------------------------------

Lorsque vous appelez une fonction, il est possible que vous ayez tous vos arguments contenus dans une liste, déjà triée correctement. Dans ce cas vous pouvez directement passer la liste entière, via un argument spécial, sans avoir à donner tous les élément un par un. Voyez cet exemple :

.. code-block:: py

    >>> def foo(a,b,c):
    ...    "Retourne a+b-c"
    ...    return a+b-c

    >>> mylist = [1,5,2]
    >>> foo(*mylist)
    4

Voyez ? Un simple astérisque, et toute votre liste est dépaquetée.

Vous pouvez faire de même avec un dictionnaire, mais avec deux astérisques. Exemple :

.. code-block:: py

    >>> mydict = {'a':1, 'c':2, 'b':5}
    >>> foo(**mydict)
    4
    # Vous pouvez même combiner avec la méthode classique :
    >>> mydict = {'a':1,'c':2}
    >>> foo(b=5,**mydict)
    4

Notez que vu que les clés d'un dictionnaire ne sont pas triées, l'ordre dans lesquelles vous les créez n'importe pas.


--------------------
Les fonctions lambda
--------------------

La plupart des développeurs débutants ont peur en voyant des fonctions lambda, aussi appelées fonctions anonymes car elles n'ont pas de nom. En effet leur syntaxe est assez étrange, difficile à décrypter selon certains. Pourtant il s'agit d'un moyen très efficace de déclarer une fonction sur une seule ligne, et qui, lorsqu'il est bien utilisé, peut vous faire gagner beaucoup de temps et de place.

La syntaxe d'une fonction lambda est donc ``lambda arguments : valeur retournée``. Un exempe, si vous voulez retourner x+2, vous ferrez ``lambda x: x+2``. D'un coup ça parrait moins compliqué non ?

Il es aussi possible de le faire avec plusieurs arguments, comme par exemple, si on reprend la fonction foo vue juste au-dessus... ``lambda a,b,c: a+b-c``.

Mais attention, comme vous pouvez l'observer, aucun nom n'est donné à cette fonction. Alors comment l'appeler ? En fait cette syntaxe retourne une fonction, donc un objet. Vous pouvez alors stocker cet objet dans une variable. Reprenons l'exemple plus haut :

.. code-block:: py

    >>> foo = lambda a,b,c : a+b-c
    >>> foo(1,5,2)
    4

Et voilà, nous avons économisé une ligne de code.


Introduction aux classes
========================

Les classes sont des sortes de types custom de variables, créées par le développeur pour un besoin spécifique. Vous en croiserez souvent, que ça soit dans des bibliothèques extérieures ou à cause d'un besoin de votre code. Elles sont extrêmement utiles, surtout dans un langage de POO, mais peuvent sembler complexes à aborder lorsqu'on débute. Je ne traiterai donc ici que d'une partie de leurs attributs, nous verrons d'autres informations plus tard.


Pour créer une classe, la syntaxe la plus minimale possible est la suivante :

.. code-block:: py

    class nom:
        pass

Vous avez donc ici une classe avec le nom 'nom', sans aucun attribut, aucune méthode, rien du tout. Une classe des plus basiques.


--------------
Initialisation
--------------

Pour commencer, nous allons y introduire des fonctions. La première à créer est la fonction ``__init__`` (notez les tirets-du-bas, très importants, deux de chaque côté), qui est appelée à chaque fois qu'une variable de cette classe est créée. Sachez aussi que *toutes* les fonctions internes à cette classe, appelées méthodes, ont pour premier argument ``self``, qui correspond à la classe elle-même. Cela vous permet d'accéder à n'importe quel autre attribut/méthode de la classe à l'intérieur d'une méthode.

La fonction ``__init__`` prend donc comme premier argument ``self``, suivi de tous les arguments que vous voulez, comme n'importe quelle fonction. Ces arguments pourront être utilisés à l'initialisation de la classe. Par exemple si vous créez une classe 'pizza', et que vous voulez noter le nombre de parts et le diamètre de la pizza, en plus de son nom, vous aurez cette syntaxe :

.. code-block:: py

    class pizza:
        def __init__(self, parts,diamètre,nom):
            self.parts = parts
            self.diam = diamètre
            self.nom = nom

Le ``self.`` permet d'enregistrer un attribut de la classe, pour le réutiliser plus tard. La fonction ``init`` peut très bien n'enregistrer aucun attribut, ou faire d'autres tâches que celle-ci, tout dépend de vos besoins.


------------
Les méthodes
------------

Maintenant, créons une méthode ``mange_part``, sans argument, qui mange une part de la pizza et affiche le nombre de parts restantes :


.. code-block:: py

    class pizza:
        def __init__(self, parts,diamètre,nom):
            self.parts = parts
            self.diam = diamètre
            self.nom = nom
        
        def mange_part(self):
            if self.parts > 0:
                self.parts -= 1
                print('Il reste',self.parts,'parts de pizza')
            else:
                print('La pizza a déjà été entièrement mangée')

On note au passage l'utilisation de ``self.parts -= 1``, qui est un raccourci pour ``self.parts = self.parts - 1``. Il existe évidemment toutes les variantes comme ``+=``, ``*=``, ``/=``, ``%=`` et j'en passe. Je vous avais déjà dit que les programmeurs étaient des fainéants ?

Bien, il ne reste plus qu'à tester notre classe :

.. code-block:: py

    >>> mapizza = pizza(2, 12.5, 'Mozzarella')
    >>> mapizza.nom
    'Mozzarella'
    >>> mapizza.mange_part()
    Il reste 1 parts de pizza
    >>> mapizza.mange_part()
    Il reste 0 parts de pizza
    >>> mapizza.mange_part()
    La pizza a déjà été entièrement mangée
    >>> mapizza.parts
    0
    >>> type(mapizza.diam)
    <class 'float'>

J'en profite pour vous montrer la classe :py:class:`type`, qui retourne la classe de la variable donnée. Très pratique pour savoir de quoi il s'agit. (Oui, on l'utilise comme une fonction alors que c'est une classe. Allez chercher la logique.)

------

Voilà, avec ce chapitre vous devriez être à un stade bien plus avancé en Python, capable de faire les premiers programmes tout seul. Amusez-vous !
