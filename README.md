# projet-proie-predateur
projet-proie-predateur

#########################################
# groupe MIASHS TD01
# David DAULASIM
# Adama KOUNDOUL
# Rina Andrianina RASOLONJATOVO
# Amélie COTTANCIN
# https://github.com/uvsq22000463/projet-proie-predateur
#########################################

Dans le cadre de notre projet,nous avons décidé de modéliser cet ecosystéme de proies et de prédateurs en une grille,
avec les predateurs en rouges et les proies en bleu.

# Travail:
Dawoud a crée le canevas puis il a codé l'apparition et la disparition des proies et il a mis les commentaires utiles à la compréhension du code ainsi que la bonne rédaction du code.
Adama s'est occupée du déplacement des proies,la création des variables et des listes ,de la reproduction des proies de toute la partie 3 et la partie 4, il s'est aussi occupée du README.

# Tout d'abord nous avons crée la grille qui provient d'un code d'un de nos professeurs.

# Les proies de départ :   
Pour le faire nous avons crée plusieurs variables proie1,proie2,proie3,proie4 qui donnent un chiffre aléatoire entre 0 et 29 (on n'a pas choisi 30 car c'est la limite)
ainsi par exemple avec (grille[proie1][proie2]) on crée une proie aléatoirement sur le terrain et aussi pour ne pas que les proies remplissent tout le terrain
on crée une variable vide qui crée une case aléatoire de couleur noire dans la grille.

# Fonctions:
On crée une fonction qu'on va nommer "tour de jeu" qui va crée à chaque tour de jeu 3 nouvelles proies dans la grille dans cette fonction et pour cela 
on créer 6 nouvelles variables (proie5,proie6,proie7,proie8,proie9,proie10) qui donnent un chiffre aléatoire entre 0 et 29 puis on a aussi les variables 
globales qui vont nous servir pour plus tard.
Vient maintenant l'heure d'ajouter les prédateurs, pour cela on a crée 2 variables pred_a et pred_b qui permettent d'ajouter aléatoirement des prédateurs sur  
le terrain et pour ne pas que les proies prennent la place des predateurs on crée une condition, prenons un exemlple pour mieux comprendre:
si on a grille[proie1][proie2] et grille[pred_a][pred_b] il ne faut pas que proie1 ne soit égale à pred_a et en même temps que proie2 ne soit pas égale à pred_b.
 
# Déplacement et reproduction des proies:
Partie1:
Nous avons crée 2 boucles for i in range,l'une pour les nombres pairs de 0 à 28 avec une marge de 2 et l'autre avec les nombres impairs de 1 à 29 avec une marge  de 2 .Plus haut nous avions crée 2 variables step et step2 qui nous donnent des chiffres aux hazard parmi 3 chiffres qui sont 1,-1 et 0 et ainsi les chiffres qui vont sortir de nos boucles vont s'aditionner avec les "step" et ainsi on met une condition qui permet pour chaque tour d'effacer la case x et et avec ses coordonnées qui se sont ajoutés aux steps, elle a une nouvelle position (la case sera de couleur bleu) au voisinage de son ancien emplacement.

Partie2:
Tout d'abord la reproduction des proies est possible que si les cases sont côte à côte et si elles le sont alors une proie apparaît sur une case aléatoire
sur leurs voisinages. On a crée deux variables proiex et pres qui font la même chose que les variables de déplacement,pour créer la condition qui permet de vérifier
si 2 proies sont côte à côte on ecrit if grille[i][t]==grille[pres][t] (à savoir que pres=i+step) alors si la condition est vraie alors on crée une proie le voisinage des deux et pour cela on prend grille[proiex][t] (sachant que proiex=i+step2) et on lui change sa couleur en bleu .

# Apparition des prédateurs:
On crée 2 variables pred1 et pred2 qui nous donnent 2 chiffres entre 0 et 29 et sans le for i in range on aurait qu'un seul predateur mais avec lui, on en a
plusieurs sur le terrain.
 
 
On a crée la variable Apro qui mesure la durée de vie des proies, ainsi pour chaque tour de jeu elle diminue de 1 et donc pour Apro=2 , on code pour faire en
sorte que les proies se déplacent sinon elles restent à la même position.
 
# Mort des proies:
Les proies meurent lorsque Apro=0 ainsi on crée 2 boucles avec les variables vide3 et vide4 qui perment de remplir le terrain en noir sauf que pour ne pas 
supprimer les prédateurs, on code en bas une boucle qui permet d'ajouter aléatoirement des cases rouges dans la grille.
 
Aprés cette étape, pour faire on sorte que les proies qui ont disparu n'apparaissent plus:
on crée 2 boucles avec les variables vide5 et vide6 qui donnent des chiffres de 0 jusqu'a 29 et avec celles-ci on va mêttre toutes les cases de la grille en noire
sauf les 3 nouvelles proies comme pour chaque tour de jeu et pour cela on a crée une condition d'inégalité entre les variables qui mettront les cases en noires et les variables qui créent les proies.
 
# Dispersion des prédateurs:
Pour les disperser on utilise le même procédé que pour la proie, on crée deux variables pred5 et pred6 qui donnent 2 chiffres entre 0 et 29
et 2 autres variables pred7 et pred8 (pred7=pred6+step, pred8=pred7 +step2) et pour ne pas d'afficher d'erreur on ne sélectionne que les pred7 et pred8 qui sont inférieurs à lim_carre.Et ainsi on supprime la case du prédateur et avec l'aide des variables pred5 et pred6 et avec les variables pred7 et pred8 on crée un nouveau prédateur.
 
# Energie des prédateurs:
Si un predateur mange une proie, son niveau d'énergie augmente de 1 représenté par la variable miam,symbolisé par la variable Epre.
Pour créer cette situation: il faut que pred7 soit égale à proie5 en même temps que pred8 soit égale à proie6 et ça sera comme ça pour toutes les proies    restantes.
  
# Niveau d'énergie suffisant:
A chaque tour de jeu Epre diminue de 1 et si le prédateur mange une proie Epre augmente de 1 ,avec Erepro qui est le niveau d'énergie minimal pour qu'une     prédateur soit crée, si Epre est supérieur ou égale à Epro alors un prédateur est crée aléatoirement sur la grille.
  
# Problème:
je n'ai pas pu créer une fonction qui permet de faire mourir les proies mais j'ai pu le faire pour Apro=-3 et -6 car c'est à ce moment que la durée de vie des 
proies est nulle. J'ai crée 2 boucles une avec la variable dead1 qui va de 0 à 4 avec une marge de 2 et une autre avec la variable dead2 qui va de 1 à 5 avec une marge ces 2 variables correspondent aux 3 premiéres proies  et ainsi avec ces variables on a transformé les 3 cases en noir avec la liste l_proie.
J'ai crée 2 boucles une avec la variable dead1 qui va de 4 à 9 avec une marge de 2 et une autre avec la variable dead2 qui va de 5 à 10 avec une marge ces 2 variables correspondent aux 3 deuxiéme proies et ainsi avec ces variables on a transformé les 3 cases en noir.
 
 
# Mort des prédateurs:
Si Epre=0 alors le niveau d'énergie des prédateurs est nulle alors pour faire disparaître les prédateurs sans faire disparaître les proies, on a mis une
condition (avec 2 variables predx et predy qui contiennent les nombres qui vont de 0 à 29) qui dit que si les coordonnées de la case des prédateurs ne sont pas
égales à ceux des proies alors ces cases seront transformés en couleur noires. Et puis on rajoute 3 proies comme pour chaque tour de jeu.
 
# Flair des prédateurs:
Nous n'avons pas pu trouvé la solution donc on l'a mis en commentaires.
On prend une boucle for i in range avec les variables i et v, on prend 2 autres variables predw et predq qui seront le résultat de l'addition entre
les différentes valeurs de la liste l_pred (liste qui enregistre les valeurs des prédateurs).
Pour vérifier qu'une proie donnée est dans l'espace d'un prédateur, il faut que sa premiére coordonnée soit suppérieur ou égale à  predw (la 1ere coordonnée du prédateur et que sa deuxiéme coordonnée à savoir l_proie[v] soit inférieur ou égale à la 2éme coordonnée du prédateur.
coordonnée soit inférieur ou égale 
