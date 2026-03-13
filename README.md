# NextBuy

**Description courte** :  
Dans le cadre du projet **NextBuy** durant notre 1ère année de Bachelor, nous avons travaillé sur le domaine de la data science avec plusieurs datasets.  
Nos missions :  
- Comprendre, explorer et filtrer les datasets : [nextbuy_eda.ipynb](./nextbuy_eda.ipynb)
- Créer des modèles de prédiction: [Pred_contenu_panier_alcool.ipynb](./Modèles/Pred_contenu_panier_alcool.ipynb), [Pred_nb_jour_avant_commande.ipynb](./Modèles/Pred_nb_jour_avant_commande.ipynb), [Pred_premier_article.ipynb](./Modèles/Pred_premier_article.ipynb)
- Visualiser les données: [nextbuy_visualisation.ipynb](./nextbuy_visualisation.ipynb)

Pour plus d'informations concernant nos choix et raisonnements pour chaque partie, consulter les ressources suivantes : 
- [Exploration et nettoyage des données](/Documentation/Exploration%20et%20nettoyage%20des%20données.md)
- [Visualisation des données](/Documentation/Visualisation%20des%20données.md)

Modèles :

- [Prédiction de la taille d'un panier pour un acheteur d'alcool](/Documentation/Modèles/Prédiction%20de%20la%20taille%20d'un%20panier%20pour%20un%20acheteur%20d'alcool.md)
- [Prédiction du nombre de jours avant une prochaine commande](/Documentation/Modèles/Prédire%20le%20nombre%20de%20jour%20avant%20une%20prochaine%20commande.md)
- [Prédiction du premier article acheté](/Documentation/Modèles/Prédiction%20du%20premier%20article%20d'un%20panier.md)

---

## 🚀 Fonctionnalités principales

- Tri et fusion de plusieurs datasets afin de créer un dataset unique et exploitable.
- Multitudes de visualisation des données facilitant la compréhension des données fournies
- Prédiction de la taille du panier d'un client ayant acheté de l'alcool : utilisation d'un modèle de prédiction par régression
- Prédiction de la taille du panier d'un client : utilisation d'un modèle de prédiction par régression


---

## 🛠️ Prérequis

- Python >= 3.10  
- Packages listés dans [requirements.txt](./requirements.txt):
    - pandas
    - numpy
    - matplotlib
    - scikit-learn
    - seaborn
    - jupyterlab==4.5.4
    - ipykernel==7.2.0
    - lightgbm==4.6.0

## 💻 Setup

__1. Cloner le dépôt:__
```bash
git clone git@github.com:EpitechBachelorPromo2028/B-DAT-201-LIL-2-1-nextbuy-4.git
cd B-DAT-201-LIL-2-1-nextbuy-4
```

__2. Créer un environnement virtuel:__
```bash
python -m venv venv
source venv/bin/activate
```

__3. Installer les dépendances:__
```bash
pip install -r requirements.txt
```

__4. Exploration:__

    - Exploration de nos différents Jupyter notebooks ainsi que notre documentation pour plus de compréhension.
