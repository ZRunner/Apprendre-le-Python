==============
Débutons enfin
==============

Nous voici arrivé au moment tant attendu de la création de notre premier algorithme. Nous allons ici explorer le monde des variables et des fonctions, qui sont à la base de la Programmation Orientée Object (POO).


----------------------
Les types de variables
----------------------

Pour ceux qui sont totalementd débutants à la programmation, il me semble nécessaire de définir ce qu'est une variable. Je dirais donc qu'il s'agit d'une boîte à chaussure, contenant une étiquette, un code-barre et un objet à l'intérieur. L'étiquette comporte le nom de la variable, qu'on utilise dans l'agorithme ; le code-barre indique à l'ordinateur où est situé sa valeur dans la mémoire vive de la machine ; et l'objet à l'intérieur est la valeur de la variable (un nombre, une chaine de caractère, une liste...).

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
