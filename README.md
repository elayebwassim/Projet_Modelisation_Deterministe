# Projet_Modelisation_Deterministe
Implémentation de solveurs numériques d'EDO (Euler, Crank-Nicholson) et ajustement par moindres carrés de modèles de dynamique des populations sur des données réelles de croissance tumorale.
# Modélisation Déterministe : Croissance Tumorale & Résolution d'EDO

## Contexte du projet
Ce projet a été réalisé dans le cadre de mon Master 1 de Mathématiques Appliquées (Université Paris-Cité), pour le cours "Équations Différentielles Ordinaires : Modélisation, Analyse, Simulations".
L'objectif était double :
1.  **Analyse Numérique :** Étudier, implémenter et comparer les performances de différents schémas numériques (Euler Explicite/Implicite, Point Milieu, Crank-Nicholson) pour la résolution d'EDO.
2.  **Modélisation Biologique (Model Fitting) :** Utiliser ces schémas pour ajuster des modèles théoriques (Malthus, Logistique, Gompertz) sur des données expérimentales réelles de croissance tumorale in vivo (cancer du poumon chez la souris).

## Technologies et Outils
*   **Langage :** Python
*   **Librairies :** NumPy, Matplotlib, SciPy (`scipy.optimize.minimize`)
*   **Concepts Mathématiques :** Équations Différentielles Ordinaires (EDO), Schémas d'intégration numérique (stabilité, consistance, convergence), Modélisation compartimentale, Optimisation par moindres carrés.

## Démarche et Implémentation

### 1. Implémentation et Comparaison des Schémas Numériques
Le projet a débuté par l'implémentation et l'analyse de l'erreur (en fonction du pas de temps $h$) de plusieurs méthodes de résolution :
*   **Schémas d'ordre 1 :** Euler Explicite et Euler Implicite (testés sur le modèle de Malthus).
*   **Schémas d'ordre 2 :** Point Milieu et Crank-Nicholson (testés sur le modèle Logistique).
*(L'implémentation des schémas implicites a nécessité la mise en place d'un algorithme de recherche de point fixe).*

### 2. Modélisation de la Croissance Tumorale (Model Fitting)
La seconde phase a consisté à confronter trois modèles théoriques de dynamique des populations aux données expérimentales fournies :
*   **Modèle de Malthus :** Croissance exponentielle illimitée.
*   **Modèle Logistique :** Croissance avec capacité de charge limite.
*   **Modèle de Gompertz :** Modèle classique en oncologie avec décroissance exponentielle du taux de croissance.

Pour chaque modèle, j'ai développé un algorithme d'optimisation (basé sur la méthode des moindres carrés via `scipy.optimize.minimize`) pour identifier les paramètres ($\lambda, r, K$) permettant à la solution numérique de s'ajuster au mieux aux points de données réels.

## Résultats et Analyse
*   L'analyse numérique a permis de confirmer empiriquement l'ordre de convergence des différents schémas implémentés.
*   L'étape d'optimisation (Model Fitting) a mis en évidence les limites du modèle de Malthus à long terme et a démontré que le modèle de Gompertz (ainsi que le modèle Logistique, dans une moindre mesure) offrait la meilleure description quantitative de la dynamique de croissance de la tumeur.

## Compétences démontrées
*   **Analyse Numérique :** Maîtrise des concepts de stabilité et de convergence des schémas de résolution d'EDO.
*   **Algorithmique :** Implémentation de solveurs d'EDO et d'algorithmes de recherche de point fixe.
*   **Data Science / Modélisation :** Capacité à formuler un problème d'optimisation (moindres carrés) pour ajuster un modèle théorique complexe sur des données empiriques réelles.
