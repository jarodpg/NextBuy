# Documentation d’étape — [Nom du projet]

## Informations générales
Nom du projet :
Prédiction de la taille du panier pour les commandes contenant de l’alcool

Responsable :  
Gabin Grebert

Date :  
13/03/2026

Étape :  
Création et entraînement du premier modèle de prédiction
---

## Objectif de l’étape
L’objectif de cette étape est de créer un modèle de machine learning capable de prédire la taille du panier d’un client lors d’une commande, en particulier lorsque celle-ci contient de l’alcool.

Le modèle doit apprendre à partir de l’historique des commandes afin d’identifier les facteurs influençant le nombre total de produits dans un panier.
---

## Contexte
Dans les données de commandes clients, plusieurs informations sont disponibles : l’heure de commande, le jour de la semaine, les produits achetés, les départements des produits, ainsi que l’historique d’achat de chaque utilisateur.

Certaines observations montrent que les commandes contenant de l’alcool peuvent être associées à des comportements d’achat spécifiques (ex : commandes du week-end ou du soir).
Il est donc intéressant de construire un modèle capable de prédire la taille totale d’un panier à partir de ces variables.

Cette prédiction peut être utile pour :

- analyser les comportements d’achat

- améliorer les recommandations produits

- optimiser la gestion des stocks ou de la logistique

---

## Actions réalisées
- Chargement et préparation du dataset des commandes (df_order_products_clean.csv)

- Création d’une variable indiquant si un produit appartient au département alcool

- Agrégation des données au niveau des commandes (order_id)

- Calcul de la taille du panier pour chaque commande

- Création de variables explicatives :

    - nombre de produits alcoolisés

    - nombre de produits réachetés

    - diversité des départements et des rayons

    - moment de la journée

    - indication week-end

- Création de variables historiques utilisateur :

    - moyenne des tailles de panier précédentes

    - taille du panier précédent

    - nombre de commandes passées

    - moyenne de réachat

- Gestion des valeurs manquantes avec la médiane globale

- Encodage des variables catégorielles avec pd.get_dummies

- Séparation du dataset en jeu d’entraînement et de test

- Entraînement d’un modèle HistGradientBoostingRegressor

- Évaluation des performances avec MAE, RMSE et R²

- Test d’optimisation des hyperparamètres avec RandomizedSearchCV

---

## Résultats
Le modèle a été entraîné avec l’algorithme HistGradientBoostingRegressor, adapté aux datasets volumineux et aux relations non linéaires.

Les performances sont évaluées avec :

    - MAE (Mean Absolute Error) : erreur moyenne de prédiction

    - RMSE (Root Mean Squared Error) : pénalise davantage les grosses erreurs

    - R² : proportion de variance expliquée par le modèle

Ces métriques permettent d’évaluer la capacité du modèle à prédire correctement la taille d’un panier.

---

## Problèmes rencontrés

- Difficulté à intégrer les informations historiques utilisateur sans introduire de fuite de données.

- Choix des hyperparamètres du modèle.

---

## Solutions apportées

- Utilisation de shift() pour éviter d’utiliser les informations de la commande actuelle

- Utilisation d’un RandomizedSearchCV pour tester différentes combinaisons d’hyperparamètres

- Choix du modèle HistGradientBoostingRegressor pour sa robustesse et ses performances sur les données tabulaires

---

## Prochaines actions

- Analyser l’importance des variables du modèle

- Créer une visualisation des prédictions vs valeurs réelles

---

## Notes

Les variables historiques utilisateur ont été calculées de manière progressive avec expanding() afin d’utiliser uniquement les informations disponibles avant la commande courante.