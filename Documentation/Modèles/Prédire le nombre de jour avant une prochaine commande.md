# Modèle de prédiction du délai entre les commandes

## Vue d’ensemble

Ce projet consiste à construire un **modèle de régression** pour prédire le **nombre de jours avant la prochaine commande d’un utilisateur**.  
Le modèle utilise les données historiques des commandes et le comportement des utilisateurs basé sur leurs achats précédents.

---

## Features principales

- **is_weekend** : commande passée un week-end ou non  
- **time_of_day** : tranche horaire de la commande (nuit, matin, après-midi, soir, soirée)  
- **user_order_count** : nombre de commandes déjà passées par l’utilisateur  
- **user_avg_days** et **user_std_days** : moyenne et écart type des délais entre commandes précédentes

## Modèle

- Objectif : prédire `days_since_prior_order` pour la prochaine commande 


## Entraînement et évaluation

- Split : 80% train / 20% test  
- Métriques : MAE, RMSE, R²  
- Le modèle capture les habitudes de commande des utilisateurs et prédit avec précision le délai avant leur prochaine commande.
