# Projet_Modelisation_Deterministe
Résolution numérique d'équations différentielles (Euler, Point Milieu, Crank-Nicholson) pour la dynamique des populations, et estimation de paramètres sur des données réelles de croissance tumorale (Malthus, Logistique, Gompertz).
# Modélisation Déterministe : Croissance Tumorale & Résolution d'EDO

## Contexte du projet
Ce projet a été réalisé dans le cadre de mon Master 1 de Mathématiques Appliquées (Université Paris-Cité). 
L'objectif était double :
1.  **Analyse Numérique :** Étudier, implémenter et comparer les performances de différents schémas numériques (Euler Explicite/Implicite, Point Milieu, Crank-Nicholson) pour la résolution d'EDO.
2.  **Modélisation Biologique (Model Fitting) :** Utiliser ces schémas pour ajuster des modèles théoriques (Malthus, Logistique, Gompertz) sur des données expérimentales réelles de croissance tumorale in vivo (évolution du volume tumoral en fonction du temps).

## Technologies et Outils
*   **Langage :** Python
*   **Librairies :** NumPy, Pandas, Matplotlib, SciPy (`scipy.optimize.minimize`)
*   **Concepts Mathématiques :** Équations Différentielles Ordinaires (EDO), Schémas d'intégration numérique (stabilité, consistance, convergence), Modélisation déterministe en dynamique des populations, Optimisation par moindres carrés.

## Démarche et Implémentation

### 1. Implémentation et Comparaison des Schémas Numériques
Le projet a débuté par l'implémentation et l'analyse de l'erreur (en fonction du pas de temps $h$) de plusieurs méthodes de résolution :
*   **Schémas d'ordre 1 :** Euler Explicite et Euler Implicite (testés sur le modèle de Malthus).
*   **Schémas d'ordre 2 :** Point Milieu et Crank-Nicholson (testés sur le modèle Logistique).
*(L'implémentation des schémas implicites pour le modèle logistique a nécessité la mise en place d'un algorithme de calcul de racines de polynômes du second degré à chaque itération du maillage).*

### 2. Modélisation de la Croissance Tumorale (Model Fitting)
La seconde phase a consisté à confronter trois modèles théoriques de dynamique des populations au jeu de données expérimentales fourni (mesures allant de 7 à 38 jours) :
*   **Modèle de Malthus :** Croissance exponentielle illimitée.
*   **Modèle Logistique :** Croissance avec capacité de charge limite (K).
*   **Modèle de Gompertz :** Modèle classique en oncologie avec décroissance exponentielle du taux de croissance.

Pour chaque modèle, j'ai développé un algorithme d'optimisation (basé sur la minimisation de l'erreur des moindres carrés via `scipy.optimize.minimize`) pour identifier les paramètres optimaux ($\lambda, r, K$) permettant à la solution numérique de s'ajuster au mieux aux points de données réels.

## Résultats et Analyse
*   **Analyse Numérique :** L'étude empirique a confirmé que les schémas d'ordre 2 (Point Milieu et Crank-Nicholson) offrent une bien meilleure précision que le schéma d'Euler implicite (ordre 1) pour un même pas de temps $h$. Le schéma du Point Milieu s'est avéré être le meilleur compromis entre précision (ordre 2) et temps de calcul (méthode explicite).
*   **Model Fitting :** L'étape d'optimisation a mis en évidence les limites du modèle de Malthus à long terme (erreur résiduelle de $\approx 403\,125$). Si le modèle de Gompertz offre une bonne description quantitative ($\approx 301\,061$), c'est le **modèle Logistique** qui a fourni le meilleur ajustement pour ce jeu de données spécifique (erreur minimale de $\approx 254\,368$), bien qu'une réserve soit émise quant à la taille restreinte de l'échantillon étudié.

## Compétences démontrées
*   **Analyse Numérique :** Maîtrise des concepts de stabilité, consistance et convergence des schémas de résolution d'EDO.
*   **Algorithmique :** Implémentation de solveurs d'EDO et d'algorithmes mathématiques (calcul de racines).
*   **Data Science / Modélisation :** Capacité à formuler un problème d'optimisation (moindres carrés) pour ajuster un modèle théorique complexe sur des données empiriques réelles.
