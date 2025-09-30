# 🌡️ Solveur Numérique 1D de l'Équation de la Chaleur (FTCS Manuel)

## 👤 Auteur
**Moussa Sow**

## 💡 Présentation du Projet
Ce projet académique est un solveur numérique pour l'**Équation de la Chaleur en une dimension** ($\frac{\partial u}{\partial t} = \alpha \frac{\partial^2 u}{\partial x^2}$). Il simule l'évolution de la température dans une barre isolée en fonction du temps et de la position.

Le code est implémenté en Python et utilise la bibliothèque `ipywidgets` pour une **interface utilisateur interactive** dans Google Colab, permettant d'ajuster les paramètres physiques et numériques.

---

## ⚙️ Méthode Numérique : Différences Finies Explicites (FTCS)

Le cœur du solveur est une implémentation **manuelle** de la méthode des **Différences Finies Explicites** (Forward-Time, Central-Space - FTCS).

### 1. Formule de Mise à Jour
La simulation procède par itération temporelle en utilisant la formule explicite, qui calcule la température au temps $k+1$ à partir des valeurs au temps $k$ :

$$u_i^{k+1} = u_i^k + r (u_{i+1}^k - 2u_i^k + u_{i-1}^k)$$

Où $r$ est le **paramètre de Fourier** : $r = \frac{\alpha \Delta t}{(\Delta x)^2}$.

### 2. Condition de Stabilité
La méthode FTCS est conditionnellement stable. Le pas de temps ($\Delta t$) est calculé pour respecter le **Critère de Von Neumann** :
$$r \leq \frac{1}{2}$$
Le code vérifie cette condition et utilise un facteur de sécurité ($dt\_factor=0.45$) pour éviter la divergence, tout en affichant un avertissement si la limite est dépassée.

### 3. Conditions aux Limites Supportées
* **Dirichlet :** Température fixe ($u$ spécifiée sur le bord).
* **Neumann :** Flux de chaleur fixe ($\partial u / \partial x$ spécifiée sur le bord ; flux nul pour l'isolation).

---

## 🚀 Utilisation (Lancement dans Google Colab)

Le moyen le plus simple d'exécuter et d'interagir avec ce projet est via Google Colab.

1.  **Ouvrir le Notebook :**
    * [Collez ici le badge "Ouvrir dans Colab"]
    * *(Pour générer le badge, utilisez le format : `[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](Lien_direct_vers_votre_fichier_ipynb_sur_GitHub)`)*
2.  Exécutez la seule cellule de code du Notebook.
3.  Utilisez l'interface **interactive** pour :
    * Définir la **Longueur**, le **Temps total** et la **Diffusivité ($\alpha$)**.
    * Choisir la **Température Initiale** (Sinusoïdale, Gaussienne, etc.).
    * Configurer les **Conditions aux Limites** à Gauche et à Droite.
4.  Cliquez sur **`Exécuter la Simulation`** (bouton vert).
5.  Cliquez sur **`Animer l'Évolution`** (bouton orange) pour voir le graphique des courbes.

---

## 📊 Analyse des Données

Pour l'analyse académique, toutes les données de la simulation (`x`, `t`, `u`) sont stockées dans la variable globale **`simulation_data`** après avoir cliqué sur **`Afficher les Données`**.

Vous pouvez ensuite utiliser une nouvelle cellule Colab pour tracer des courbes spécifiques, par exemple :

```python
# Tracer le profil de température au temps final
plt.plot(simulation_data['x'], simulation_data['u'][-1, :], label='Température Finale') 
plt.show()
