# 📊 Prédiction et Comparaison de Modèles

## 1. Description du projet
Ce notebook a pour objectif de **prédire le premier article ajouté dans un panier** à partir des données de commandes clients.  
Il inclut plusieurs étapes clés :
- Feature engineering
- Entraînement de différents modèles de machine learning
- Évaluation et comparaison des modèles

---

## 2. Dataset
Le dataset utilisé est issu de l'étape précédente de nettoyage et de fusion ce qui lui permet avant toute création de nouvelles colonnes de contenir ces suivantes :
- `order_id` : identifiant unique de la commande  
- `user_id` : identifiant de l’utilisateur  
- `product_name` : nom du produit
- `product_id` : id du produit
- `departments` : catégorie principale du produit
- `aisles` : sous catégorie de produit
- `add_to_cart_order` : l'ordre d'ajout des produits dans le panier
- `reordered` : si le produit est acheté une première fois ou recommandé
- `order_number` : numéro de la commande de l’utilisateur  
- `order_dow` : jour de la semaine de la commande  
- `order_hour_of_day` : heure de la commande  
- `days_since_prior_order` : jours depuis la dernière commande

---

## 3. Préparation des données pour l'entrainement
Afin d'ajouter de la précision dans nos résultats, nous avons effectué plusieurs actions :
- Création d'une colonne indiquant la taille du panier
- Filtrage afin de conserver uniquement les premiers articles étant ajoutés au panier
- Création d'une colonne indiquant le nombre de vente total de chaque produit
- Création d'une colonne indiquant le nombre de fois où chaque article a été vendu en étant le premier ajout du panier
- Création d'une colonne indiquant la probabilité que le produit soit ajouté en premier

---

## 4. Features
- `reordered`,
- `order_number`,
- `order_dow`,
- `order_hour_of_day`,
- `days_since_prior_order`,
- `cart_size` : taille du panier
- `product_sales_nb` : nombre de ventes total pour le produit
- `product_sales_in_first_nb` : nombre de ventes en 1ère position pour le produit
- `sales_in_first_prob` : probabilité que l'article soit ajouté en premier

La création des 4 dernières colonnes sont celles qui nous ont permis d'accroître nos résultats mais nous avons cependant un petit doute. En effet, à la suite de la création de `product_sales_nb` et `product_sales_in_first_nb` nos metrics ont favorablement explosé ce qui nous pensons peut-être un cas de data leakage.

---

## 5. Target
`product_id` : id du produit, déjà en valeur numérique contrairement au `product_name` et donc gain de temps en se passant d'un encodeur

---

## 6. Modèles utilisés
### a. Pour prédire à partir de l'ensemble des produits vendus en 1ère position
Une chose était sûre, c'est que nous allions utiliser un modèle de classification puisque nous cherchions à prédire une catégorie et non une quantité. 

Au départ, selon la cheat sheet de scikit-learn nous avons décidé d'employer le modèle SGDClassifier qui est adapté au gros dataset comme le nôtre. Le problème étant que la prédiction se base sur 35 128 classes, nos produits possibles, ce qui rendait l'entrainement du modèle infiniment long même en optimisant ses hyper-paramètres et nos features (la fonction get_dummies() était appliquée seulement sur une feature).  

Après avoir testé de multiples modèles, le seul qui a su nous fournir un résultat en exploitant la totalité des produits possibles a été le `KNeighborsClassifier` qui contre toutes attentes obtient une "accuracy" de 75%.

### b. Pour prédire à partir de l'ensemble des produits ayant plus de 50% de chance d'être vendus en 1ère position
Le but de ce projet était de comparer différents modèles afin de probablement découvrir le machine learning et ses possibilités. Pour ce faire nous avons filtrer une fois encore notre dataset en gardant uniquement les produits ayant plus de 50% de chance d'être achetés en premier.  

Cela nous permet de passer de 35 128 classes prédictibles à 424.  

Ainsi, nous avons pû comparer les modèles suivants :

| Modèle | Description |
|--------|-------------|
| `KNeighborsClassifier` | Classificateur basé sur les k plus proches voisins |
| `SGDClassifier` | Classificateur linéaire utilisant la descente de gradient stochastique |
| `LightGBM` | Gradient boosting optimisé pour la vitesse et la précision |

> Chaque modèle est entraîné sur les mêmes features et évalué avec les mêmes métriques pour assurer une comparaison juste.

**Conclusion :** Dans notre cas bien que les résultats soient biaisés par notre trop grands nombre de classes, le modèle étant le plus performant semble être le `LGBMClassifier` qui performe mieux selon nos metrics utilisées.

---

## 7. Évaluation des modèles
Les performances des modèles sont mesurées à l’aide de métriques adaptées aux **problèmes de classification**:
- Accuracy  
- Precision  
- Recall  
- F1-score