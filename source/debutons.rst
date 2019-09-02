==============
Débutons enfin
==============

Nous voici arrivé au moment tant attendu de la création de notre premier algorithme. Nous allons ici explorer le monde des variables et des fonctions, qui sont à la base de la Programmation Orientée Object (POO).

Avant toute chose, il est nécessaire de préciser deux trois points sur Python :

- Le langage est sensible à la casse : la variable ``Test`` est différente de la variable ``test`` ou même ``TEST``! De même, ``True`` existe mais pas ``true``.
- Un appel de fonction doit toujours se faire avec des parenthèses, même si aucun argument n'est donné. Sinon vous renvoyez la fonction en elle-même, en tant que variable, sans l'appeler.
- L'indentation est **extrêmement** importante en Python. Là où certains langages pourraient se faire en une seule ligne en abusant des points-virgules ou des accolades, la syntaxe de Python est majoritairement définie par l'indentation. Vous *devez* indenter votre code lorsque vous êtes dans un bloc, sinon Python ne pourra même pas lire votre programme !

Ces recommandations faites, je vous propose d'entammer l'apprentissage des variables. C'est parti !


----------------------
Les types de variables
----------------------

Pour ceux qui sont totalement débutants à la programmation, il me semble nécessaire de définir ce qu'est une variable. Je dirais donc qu'il s'agit d'une boîte à chaussure, contenant une étiquette, un code-barre et un objet à l'intérieur. L'étiquette comporte le nom de la variable, qu'on utilise dans l'agorithme ; le code-barre indique à l'ordinateur où est situé sa valeur dans la mémoire vive de la machine ; et l'objet à l'intérieur est la valeur de la variable (un nombre, une chaine de caractère, une liste...).

Il existe plusieurs types de variables en Python, en fait même une infinité puisqu'il est possible de définir son propre type (aussi appelé 'classe'). Nous ne verrons pour le moment que les plus communs.

1. Les entiers (``int``) sont.... des nombres entiers, positifs ou négatifs. Que ça soit -2, 7 ou 1e99 (1x10^99), tous sont stockés sous le même type *integer*. Il est évidemment possible de les additionner ``+``, soustraires ``-``, multiplier ``*``, diviser ``/`` etc. ensembles, en plus d'autres opérations plus complexes (division entière ``//``, modulo ``%``...)
2. Les chaines de caractères (``str``), tout aussi simple à deviner, sont des sortes de listes de caractères. Définies entre guillemets ``"abc"`` ou simples apostrophes ``'def'``, elles peuvent contenir un grand nombre de caractères, ou aussi être vides. Vous pouvez facilement les concaténer avec le symbole ``+``, et accéder à un caractère particulier de la même manière que pour une liste. Elles ont aussi leurs propres méthodes que nous verrons plus tard.
3. Les réels (``float``) sont des nombres ayant une partie décimale, aussi bien positifs que négatifs. Ils peuvent par exemple être issus d'une division de deux entiers, comme 5/2. Tout comme les entiers, la plupart des opérations mathématiques communes leurs sont appliquables. Contrairement à certains autres langages, les *double* n'existent pas, et les *float* représentent une plus grande portion de nombres.
4. Les listes (``list``) sont parfois appelés tableaux ailleurs. Il s'agit d'une liste d'éléments ordonnés, possédant des méthodes pour insérer, supprimer ou accéder à une valeur. Une liste peut contenir plusieurs types d'éléments différents, et n'a pas de taille fixe, ce qui la rend très modulable. De plus vous pouvez concaténer deux listes ensemble avec l'opérateur ``+``. Attention à ne pas confondre avec les ``tuple``, qui eux sont des listes ne pouvant pas être modifiées après création.



----------------------
Utiliser des variables
----------------------

Maintenant que vous savez la base sur les variables, il est temps d'apprendre à les utiliser. Pour cela rien de plus simple, il suffit de suivre la syntaxe ``nom = valeur``. Par exemple le code ``test = 12`` va créer une variable nommée 'test' de type 'integer' avec pour valeur '12'. Et c'est tout !

Un autre truc cool avec Python, c'est que les variables n'ont pas de type assigné : si juste après vous mettez ``test = ['a','b','c']``, dans ce cas la variable test précédemment créée va devenir une liste avec trois chaines de caractères, et perdre sa valeur précédente. Simple, non ?

Il est aussi possible de convertir certains types de variables en d'autres types, par exemple ``int('12')`` retournera l'entier 12, et ``list("abc")`` retournera la liste ``['a','b','c']``. Si vous voulez que votre variable ``test`` ayant pour valeur l'entier 12 soit d'un coup une chaine de caratère de la même valeur, il suffit de taper ``test = str(test)``, et le tour est joué. Je vous laisse réfléchir à la puissance de ce que cela implique.

Maintenant jouons à un petit jeu. Essayez de deviner la valeur et le type de la variable `c` à la fin de l'algorithme ci-dessous.

.. code-block:: python

    a = 12
    b = -9
    c = a + b
    c = "b" + str(c)

Vous avez trouvé ? Il s'agit de la chaine de caractère 'b3' : à la troisième ligne c prend la valeur ``12 + (-9)`` soit 3, et juste après on lui dit de prendre le caractère ``"b"`` à laquelle on accole ``"3"``.  
Un peu tordu ? Alors n'hésitez pas à relire autant qu'il le faut, car ce n'est que le début.


---------------------------------
Quelques mots-outils sympathiques
---------------------------------

Comme dans tout langage de programmation, il y a des mots clés qui permettent de définir la structure de l'algorithme : définir une fonction, utiliser une boucle, ajouter une condition... ils vous seront indispensables à la création de votre code. Voici les plus fréquents.

La boucle FOR
-------------

.. code-block:: py

    for <variable> in <itérateur>:
        # some code

La boucle ``for`` permet d'exécuter un bloc de code un certain nombre de fois, avec une variable prenant à chaque tour une nouvelle valeur contenue dans un itérateur (une liste par exemple). C'est à dire que si j'utilise par exemple ``for jour in ['lundi','mardi','mercredi']``, le bloc de code va s'exécuter trois fois, et la variable ``jour`` prendra tour à tour les valeurs 'lundi', 'mardi' et 'mercredi'. 

Si le but n'est que d'exécuter la boucle un nombre précis de fois, la fonction ``range(i)`` permet de générer un itérateur allant de 0 à i-1. D'autres arguments sont disponibles pour cette fonction, comme nous le verrons plus tard. Par exemple pour avoir une boucle avec un incrément ``i`` s'incrémentant trois fois, il faudra ``for i in range(3)``.


La boucle WHILE
---------------

.. code-block:: python

    while <condition>:
        # some code

Cette boucle est, à l'inverse de la boucle for, utilisée lorsqu'on ne connait pas le nombre précis d'itérations. Dans ce cas on se sert d'une condition, et "tant que" cette condition est vraie, alors le bloc s'exécutera. Attention à surveiller cette condition, car il est très simple de créer une boucle infinie qui ne s'arrêtera jamais ! D'ailleurs dans certains cas le programme requiers une boucle infinie, qui est cassée à un moment précis par le mot-clé ``break`` (cf plus bas). On utilise alors ``while True``, vu que True retournera toujours True...


Les conditions (IF/ELSE)
------------------------

.. code-block:: python

    if <condition>:
        # some code
    else:
        # some other code

Le mot-clé IF, traduit par "Si" en français, permet d'exprimer une condition : 'Si' la condtion est vraie, alors exécute ce code. Il est *possible* (mais non obligatoire) de le faire suivre d'un bloc ELSE, qui va exécuter du code si la condition est fausse. Très intuitif, non ?

Mais que se passe-t-il si on veut tester la valeur d'une variable, qui peut prendre plusieurs valeurs différentes ? Le premier réflexe serait d'enchaîner les blocs if/else, un peu comme dans cet exemple :

.. code-block:: python

    if jour == "lundi":
        print("Premier jour !")
    else:
        if jour == "mardi":
            print("Deuxième jour !")
        else:
            if jour == "mercredi":
                # etc.

Mais vous devez vous en rendre compte, cette syntaxe est loudre et génère de grosses indentations. Et les développeurs sont connus pour leur fainéantise, alors ils ont inventé le mot-clé ELIF, contraction de Else If... dont voici un exemple :

.. code-block:: python

    if jour == "lundi":
        print("Premier jour !")
    elif jour == "mardi":
        print("Deuxième jour !")
    elif jour == "mercredi":
        # etc

Il est bien évidemment possible de finir avec un bloc ELSE, qui est utilisé pour tous les cas restants (si aucune condition n'est vérifiée).


Les trucs à utiliser à l'intérieur d'une boucle
-----------------------------------------------

Deux mots-clés sont important à connaître lorsqu'on manipule les boucles. Il y a tout d'abord ``break``, dont j'ai fait mention un peu plus haut, qui permet d'arrêter immédiament une boucle. Par exemple ces deux boucles sont identiques :

.. code-block:: py

    while True:
        # some code
        if jour == "dimanche":
            break
    
    while jour != "dimanche":
        # some code
    
Vous remarquerez l'utilisation de l'opération ``!=``, qui signifie "est différent de", à l'inverse de ``==`` (égal à).

L'autre mot-clé est ``continue``, qui arrête l'itération de la boucle uniquement : tout le code jusqu'à la fin de l'itération est alors ignoré, et la boucle refait un tour. Voici un exemple, exécuté dans le terminal :

.. code-block:: py

    >>> for i in range(5):
    ...    if i == 2:
    ...        continue
    ...    print(i)

    0
    1
    3
    4

Lorsque ``i`` a prit pour valeur 2, la condition du 'if' s'est vérifiée, le mot-clé 'continue' a été appelé, et donc le reste de l'itération a été ignoré.


-------------
Les fonctions
-------------

Les fonctions sont une composante essentielle de la programmation. Il s'agit d'un bout de code réutilisable plusieurs fois, à plusieurs endroits différents du code. Voici sa syntaxe dans la forme la plus complète :

.. code-block:: py

    def nom(argument:classe dargument) -> classe de retour:
        "Description de la fonction"
        # some code
        return valeur

    # Exemple :
    def addition(a:int, b:int) -> int:
        """Additionne deux nombres et retourne leur somme
        a : nombre entier
        b : nombre entier
        Retour : nombre entier"""
        return a+b

Il n'est pas nécessaire d'être aussi exhaustif, en soit Python se contente de ceci, bien moins lisible pour un développeur externe, mais tout aussi fonctionnel :

.. code-block:: py

    def addition(a,b):
        return a+b

Il est même possible de définir une fonction qui ne demande pas d'argument, ou qui ne retourne rien du tout. Il suffit dans le premier cas de ne rien mettre entre les parenthèses, et dans le deuxième cas de ne pas utiliser le mot-clé ``return``.

Pour avoir de l'aide sur une fonction, que ça soit une fonction incluse dans Python, ou une venant d'une bibliothèque importée, ou même une créée par vous, vous pouvez appeler la fonction ``help()`` en donnant le nom de la fonction en argument. Tenez, ouvrez Python et entrez ``help(print)`` pour voir la syntaxe et la description de la fonction. Ensuite, je vous invite à définir vos propres fonctions pour tester avec celles-ci. Faites vos expériences !

A propos de la fonction ``help``... il est possible de l'appeler sans argument, auquel cas elle affichera l'aide de Python en général et vous proposera de vous guider dans son menu. Ou vous pouvez demander de l'aide sur un mot-clé de Python, en lui donnant comme paramètre la chaine de caractère correspondante (essayez ``help("pass")``).
