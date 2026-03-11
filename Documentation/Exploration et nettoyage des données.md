# Documentation d’étape — Exploration et nettoyage des données — NextBuy

## Contexte et objectif
Le but du projet NextBuy à savoir exploiter des données afin d'effectuer des prédictions nécessite tout d'abord d'avoir un jeu d'informations "propres" pour en tirer les meilleurs résultats. En effet, la présence de valeurs nulles, aberrantes ou en double auront pour impact de fausser les résultats obtenus ou bien de provoquer des erreurs. De plus, face à une masse de données brutes et non synthétisées, il convient de se poser des questions pertinentes à propos de leur traitement et de leur éventuelle mise en relation dans le but d'orienter nos futurs réalisations.  

Cette étape s'impose alors comme les prémices de notre projet en instaurant une base saine et en fixant des objectifs de travail.

---

## Questions de cadrage
Après avoir analyser et compris l'ensemble des datasets fournis nous avons choisi de mettre en place 11 questions qui, à notre sens, sont pertinentes dans l'interprétation des données. Celles-ci peuvent par exemple amener l'enseigne commerciale à adopter certaines mesures afin de maximiser ses bénéfices. Pour ce faire, nous avons créer des questions allant du plus général au plus spécifique en en instaurant 3 de plus que demandé (8 au minimum). Cela nous permet d'avoir une marge de manoeuvre dans le cas où nous serions en incapacité d'y répondre à toutes.

---

## Observations des données
Avant de nettoyer les datasets nous avons pris l'initiative d'analyser les erreurs possibles pour ensuite connaitre exactement les éléments à supprimer.  

Pour ce faire, nous avons procéder de manière méthodique en parcourant chacune des colonnes des datasets en émettant des hypothèses concernant les erreurs possibles.  

Par exemple, pour l'ensemble des ID nous avons vérifié s'ils étaient bien tous positifs et supérieurs à 0. Par conséquent, nous avons réaliser un filtre sur le dataset originel pour ne garder que les ID ne respectant pas ces conditions puis nous avons renvoyer la taille du dataset une fois filtré. Si le chiffre renvoyé vaut 0, alors cela veut dire qu'une fois filtré le dataset ne contient aucun ID ne respectant pas ces conditions et qu'il n'y a donc pas besoin de nettoyer cette colonne.  

La procédure a ensuite été la même pour le reste des datasets avec bien sûr un filtre différent appliqué en fonction du type de donnée analysé. Par exemple, pour analyser la colonne "add_to_cart_order" nous avons également vérifier que pour une même commande il n'y avait pas deux fois la même valeur ce qui signifierait que deux articles ont potentiellement été ajoutés en même temps.

---

## Actions réalisées
Après avoir observé les erreurs présentes nous avons appliqué les mesures spécifiques permettant de les corriger :

Nettoyage order_product.csv :
- dropna
- conversion en entier

Nettoyage orders.csv :
- dropna
- conversion en entier

Nettoyage products.csv :
- conversion en entier et str
- décodage des entités HTML
- suppression des product_name en double de manière case insensitive

Fusion en un dataset :
- Fusion des departments et aisles ID dans products.csv pour en récupérer les noms
- Fusion des orders et products ID dans order_products.csv pour en récupérer l'ensemble des informations et grouper le tout en un dataset facilement exploitable

---

## Résultats
Au final nous obtenons un seul dataset issu de la fusion de tous ceux fournis grâce à l'utilisation des ID présents. Selon nous, avoir un unique dataset était la solution la plus pratique à exploiter dans le futur notamment pour la conception de nos modèles de prédiction. En effet, cela évite de sans cesse interagir entre les cinq datasets fournis et permet de gagner en confort dans la réalisation de nos codes. Celui-ci comprend 12 811 680 lignes et 11 colonnes puisque trois sont maintenant inutiles après la fusion : "aisle_id", "department_id", "product_id". Enfin, l'ensemble des données problématiques observées ont été traitées ce qui en fait un dataset pleinement utilisable pour la suite du projet.

---

## Problèmes rencontrés
Le questionnement majeur à propos de nos actions est surtout la méthode employée pour analyser les valeurs aberrantes, manquantes ou problématiques avant d'effectuer le nettoyage. En effet, nous avons utilisé une méthode "binaire" qui consiste à réaliser un "print" du dataset filtré autant de fois qu'il y a de conditions à vérifier. Cela apparaît alors extrêmement long et pourrait être problématique dans un projet où le temps imparti est très court.  

Ensuite, la création de questions pertinentes n'a pas été simple puisqu'il a d'abord fallu comprendre totalement les cinq datasets qui se complètent les uns des autres. Une cellule intituler "Questions commerciales" est d'ailleurs présente et montre que nous avons dû passer par du code pour analyser les données et former la question 11. Nous ne savons pas également si nous pourrons apporter une réponse à chacune de nos questions et c'est pour quoi nous avons créer 11 questions sur 8 imposées au minimum.

---

## Prochaines actions
Si d'autres valeurs apparaissent non normalisées à la suite du projet, il faudra revoir le nettoyage des datasets afin de reproduire une base exploitable.