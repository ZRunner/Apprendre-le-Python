========================
Solution à l'exercice 1
========================

Voici mes deux propositions pour l'exercice du pendu, première version :

Version 1
---------

.. code-block:: python

    mot = "python"

    print("Bienvenue dans le jeu du Pendu ! Vous avez 7 tentatives pour deviner un mot secret. Ce mot comporte 5 lettres. Bonne chance !")
    proposition = ""
    for i in range(7):
        proposition = input("Tentative numéro "+str(i+1)+" : ")
        if proposition == mot:
            print("Bien joué ! Vous avez gagné !")
            break
        else:
            print("Raté !")
    print("Fin de la partie")


Version 2
---------

.. code-block:: python

    mot = "python"

    print("Bienvenue dans le jeu du Pendu ! Vous avez 7 tentatives pour deviner un mot secret. Ce mot comporte 5 lettres. Bonne chance !")
    proposition = ""
    tentatives = 1
    while tentatives <= 7:
        proposition = input("Tentative numéro "+str(tentatives)+" : ")
        if proposition == mot:
            print("Bien joué ! Vous avez gagné !")
            break
        else:
            print("Raté !")
        tentatives = tentatives + 1
    print("Fin de la partie")

Il existe une infinité d'autres solutions, et du moment qu'elle fonctionne, pour le moment nous ne ferons pas attention. Plus tard, lorsque vous ferez de longs algorithmes avec des milliers de lignes, il faudra prendre garde aux deux facteurs de 'complexité' : le temps d'exécution, et la mémoire utilisée.
