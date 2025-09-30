# 🌡️ Solveur Numérique 1D de l'Équation de la Chaleur (FTCS Manuel)

## 👤 Auteur
**Moussa Sow**

## 💡 Présentation du Projet
Ce projet académique est un solveur numérique pour l'**Équation de la Chaleur en une dimension** ($\frac{\partial u}{\partial t} = \alpha \frac{\partial^2 u}{\partial x^2}$). Il simule l'évolution de la température dans une barre isolée en fonction du temps et de la position.

Le code est implémenté en Python et utilise la bibliothèque `ipywidgets` pour une **interface utilisateur interactive** dans Google Colab.

---

## 🚀 Utilisation (Lancement dans Google Colab)

Le moyen le plus simple d'exécuter et d'interagir avec ce projet est via Google Colab.

### 1. Accès au Notebook
**Ouvrez le simulateur directement dans Colab :**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SHERLOCKSOW/Heat-Equation-1D-FTCS/blob/main/heat_equation_par_moussa_sow.ipynb)

*Le fichier du solveur est :* `heat_equation_par_moussa_sow.py` (ou `.ipynb`)

### 2. Étapes de Simulation
1.  Exécutez la seule cellule de code du Notebook après l'avoir ouvert.
2.  Utilisez l'interface **interactive** pour ajuster les paramètres physiques et numériques.
3.  Cliquez sur **`Exécuter la Simulation`** (bouton vert).
4.  Cliquez sur **`Animer l'Évolution`** (bouton orange) pour visualiser le profil de température au fil du temps.

---

## ⚙️ Détails de la Méthode Numérique : Différences Finies Explicites (FTCS)

### Formule de Mise à Jour
Le cœur du solveur est une implémentation **manuelle** de la méthode FTCS :

$$u_i^{k+1} = u_i^k + r (u_{i+1}^k - 2u_i^k + u_{i-1}^k)$$

Où $r$ est le **paramètre de Fourier** : $r = \frac{\alpha \Delta t}{(\Delta x)^2}$.

### Condition de Stabilité
La stabilité est garantie si le **Critère de Von Neumann** est respecté : $r \leq \frac{1}{2}$. Le code calcule $\Delta t$ pour satisfaire cette condition mais affichera un avertissement en cas de paramétrage instable.

### Conditions aux Limites Supportées
* **Dirichlet :** Température fixe ($u$ spécifiée).
* **Neumann :** Flux de chaleur fixe ($\partial u / \partial x$ spécifiée).

---

## 📊 Analyse des Données

Pour l'analyse académique, les données complètes de la simulation (`x` : position, `t` : temps, `u` : matrice de température) sont stockées dans la variable globale **`simulation_data`** après avoir cliqué sur le bouton **`Afficher les Données`**.

Ceci permet de générer des **courbes personnalisées** dans une cellule de code séparée pour l'analyse des profils de température et de l'évolution temporelle.

```python
# Exemple d'accès aux données dans Colab :
import matplotlib.pyplot as plt
# Assurez-vous d'avoir exécuté la simulation !
# plt.plot(simulation_data['x'], simulation_data['u'][-1, :], label='Température Finale') 
# plt.show()
