# Documentation d’étape — Visualisation des données — Next Buy

## Objectif de l’étape

Une fois le nettoyage de l'ensemble des données fournies effectué, nous avons procédé à la visualisation de celles-ci. En effet, nous avons cherché à produire des graphiques, des diagrammes et d'autres types de visualisations qui nous semblaient pertinents afin de comprendre plus en profondeur le jeu de données et de répondre aux questions que nous nous sommes posées.
---

## Actions réalisées

Tout d'abord, nous avons créé 11 catégories reprenant chacune nos questions de la partie "Exploration et nettoyage". Ensuite, nous avons manipulé les lignes et colonnes de notre dataset afin d'en tirer des informations répondant à nos attentes :

1. Réalisation du compte de nombre de vente par produit dans le but d'en extraire les 10 plus importants.  
CCL : Les bananes sont de loin le produit le plus vendu.

2. Réalisation du compte de nombre de vente par produit dans chaque "department". A la suite de ceci nous avons extrait l'article le moins vendu et l'article le plus vendu pour chacune des catégories puis avons représenté ses informations sous forme de diagramme en bâtons groupés. Deux échelles distinctes sont présentes : à gauche le nombre de vente pour les produits les moins populaires et à droite le nombre de vente pour les produits les plus populaires. Ceci permet de distinguer la quantité d'articles vendus parmi les moins populaires car avec une unique échelle leurs représentations étaient minuscules aux côtés des articles les plus vendus (souvent 1 vente contre plusieurs milliers, ce qui rendait "invisible" la barre représentant le nombre de vente valant 1).

6. - Visualisation du nombre de vente par "department". CCL : La catégorie "produce" domine largement la scène avec plus de 3 500 000 ventes.
    - Heatmap du nombre de commande par department et par jour de la semaine. CCL : Dimanche et lundi semble être les jours cumulant le plus de ventes parmi chacune des catégories.
    - Représentation du nombre de commandes par heure. CCL : La tranche horaire cumulant le plus de ventes s'étend entre 10H et 15H.
    - Représentation du nombre de commandes par heure pour la catégorie des produits surgelés. CCL : Notre observation précédente se confirme pour le department "frozen" et peux laisser penser qu'il en est de même pour les autres catégories.

8. Représentation de la relation entre les premiers articles achetés et les deuxièmes. Chaque carré rouge montre un duo de produits achetés en premier et deuxième choix. CCL : Ce graphique aurait pu être intéressant si un duo revenait plus d'une fois et pour cela il aurait fallu traiter l'ensemble des commandes de notre dataset. Cependant, au vu du nombre de produit très élevé la heatmap deviendrait illisible. Pour résoudre ce problème il faudrait garder uniquement les duo présent plus d'une fois puis reconstruire une heatmap.

9. Représentation du nombre de vente par heure pour la catégorie "alcool". CCL : Une fois de plus, le plus grand nombre de vente s'effectue également entre 10 et 15H avec un pic légèrement plus important à la fin de cet intervalle.
---

## Résultats

L'ensemble des visualisations sont accessibles dans le fichier [nextbuy_visualisation.ipynb](nextbuy_visualisation.ipynb).
---

## Problèmes rencontrés

Nous avons rencontré plusieurs problèmes, notamment le fait que les datasets aient une taille conséquente. Cela à d'abord pour effet de compliquer le choix des données à manipuler pour obtenir un résultat intéressant mais provoque aussi régulièrement un long temps de chargement lorsque des actions sont effectuées (création d'une nouvelle colonne ou d'un nouveau dataset, utilisation de fonctions telles que "groupby()", "value_counts()", etc ).
---