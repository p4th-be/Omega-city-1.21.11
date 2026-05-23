# 🏙️OMEGA CITY  — v1.21.3 
### Un jeu de construction de ville (city-builder) jouable entièrement dans le navigateur, sans installation ni dépendance externe. Un seul fichier HTML suffit.

______________
# 🚀lancement
Ouvre simplement `omega_1_21_3.html` dans n'importe quel navigateur moderne (Chrome, Firefox, Edge, Safari, Opera, Opera gx, même sur internet explorer, mais attend mais qui utilise encore internet explorer???).

Aucun serveur, aucune installation requise.

____
# 🎮 Modes de jeu
| Mode | Argent de départ | Particularité |
|------|-----------------|---------------|
| **Normal** | 2 000 € | Économie stricte, arbre technologique actif. Tu es un maire débutant c'est facile de déveloper ta ville. |
| **Difficile** | 500 € | Entretien +50 %, exports d'énergie −50 %, taxes −20 %, clics −50 % Tu es un vrai maire c'est pas facile de déveloper ta ville avec toutes les taxes. |
| **Créatif** | Infini | Sandbox libre, toutes les technologies débloquées, pas de coûts Tu es un maire c'est facile de déveloper ta ville avec ton imagination. |

---

## 🖥️ Interface
![This is an alt text.](https://i.ibb.co/Xf6CMzvh/jeu.png "This is a sample image.")

---

## 🏗️ Bâtiments

### Infrastructures
| Icône | Nom | Coût | Effet |
|-------|-----|------|-------|
| 🛣️ | Route | 50 € | Connexion des tuiles |
| 🧨 | Détruire | Gratuit | Supprime un bâtiment |

### Habitations (génèrent population et taxes)
| Icône | Nom | Coût | Pop | Taxes/s |
|-------|-----|------|-----|---------|
| 🏠 | Cabane | 200 € | 6 | 900 € |
| 🏡 | Pavillon | 500 € | 16 | 1 200 € |
| 🏢 | Immeuble | 1 200 € | 215 | 3 500 € |

### Production d'énergie
| Icône | Nom | Coût | Production | Technologie requise |
|-------|-----|------|-----------|---------------------|
| 🔥 | Centrale Charbon | 1 000 € | 80 | — |
| 🌀 | Éolienne | 1 500 € | 700 | Écologie |
| ☀️ | Solaire | 3 500 € | 300 | Écologie |
| 💦 | Turbine à vagues | 3 000 € | 550 | Océan |
| ☢️ | Nucléaire | 10 000 € | 500 | Usinage |
| ⚛️ | Accélérateur de particules | 1 000 000 000 € | 1 000 000 | Militaire Avancé |

### Services & Bonheur
| Icône | Nom | Coût | Effet |
|-------|-----|------|-------|
| 🏫 | École | 4 000 € | Science +3/s |
| 🌳 | Parc | 1 000 € | Bonheur +5 |
| ⚽ | Stade | 8 000 € | Bonheur +50 |
| 👮 | Police | 3 000 € | Bonheur +10 |
| 🧬 | Centre de Recherche | 5 000 € | Science +30/s |
| 🧪 | Super Labo | 15 000 € | Science +70/s |

### Industrie & Finance
| Icône | Nom | Coût | Taxes/s |
|-------|-----|------|---------|
| 🏧 | Petite banque | 10 000 € | 100 000 € |
| 💳 | Banque | 100 000 € | 1 000 000 € |
| 💶 | Banque municipale | 150 000 € | 1 500 000 € |
| 💻🏭 | Usine de PC | 28 000 € | 10 000 € |
| 👽 | Zone 51 | 1 000 000 € | 100 000 € |

### Militaire (nécessite tech Militaire)
| Icône | Nom | Coût |
|-------|-----|------|
| 🔈 | Petite base militaire | 7 000 € |
| 🔉 | Base militaire | 14 000 € |
| 🔊 | Grande base militaire | 28 000 € |
| 🛫 | Aérodrome | 28 000 € |
| 🚫 | Système antidrone | 15 000 € |

### Nature (nécessite tech « La route vers la nature »)
| Icône | Nom | Effet pollution |
|-------|-----|-----------------|
| 🌊 | Océan | — |
| 🏖️ | Étang | −10 |
| 🌅 | Mer | −30 |
| 🌳 | Forêt | −15 |

---

## 🔬 Arbre Technologique

<a href="https://ibb.co/sJgQksY6"><img src="https://i.ibb.co/vvcmgLnQ/Screenshot-2026-05-22-09-56-43.png" alt="Screenshot-2026-05-22-09-56-43" border="0"></a>

Les technologies se débloquent avec des **points de science** (🧪), générés par les écoles et labos.

---
## 📊 Économie

Le revenu par seconde est calculé ainsi :

```
Revenu net = Taxes des bâtiments + Export d'énergie − Entretien
```

- **Export d'énergie** : chaque unité d'énergie excédentaire rapporte 3 €/s (désactivé en mode Créatif).
- **Entretien** : chaque bâtiment a un coût fixe par seconde.
- **Bouton cliqueur** : génère un revenu immédiat basé sur `50 + (population × 2) + (science × 1)`.

### Indicateurs surveillés
| Indicateur | Impact négatif si... |
|------------|----------------------|
| **Satisfaction** | < 40 % (rouge) — chute si pollution élevée ou chômage > 70 % |
| **Emplois** | < 30 % de la population → −15 de satisfaction |
| **Pollution** | Chaque unité retire 2 points de satisfaction |
| **Énergie** | Bâtiment sans courant = inactif (bordure rouge) |
| **Travailleurs** | Bâtiment sans main-d'œuvre = inactif (bordure orange) |

---

## ⚙️ Architecture technique

Le jeu est entièrement contenu dans **un seul fichier HTML** (~1 300 lignes) organisé en modules JavaScript :

| Module | Rôle |
|--------|------|
| `base de données` | Base de données des bâtiments et technologies |
| `état` | État global du jeu (argent, grille, mode, etc.) |
| `jeu` | Boucle principale, démarrage, clics |
| `placement` | Rendu canvas, gestion de la caméra, placement |
| `Simulation` | Calcul population, énergie, taxes, pollution |
| `interface` | Mise à jour de l'interface, menus, arbre tech |
| `journal` | Journal d'événements en bas de l'écran |

La grille est de **60 × 60 tuiles** (32 px chacune). La propagation de l'électricité utilise un **algorithme BFS** depuis les sources d'énergie.

---
## 📝 Notes de version 1.21.3

### nouveau!!
- la grille est maintenant bougeable sur tout les apareils
- le probleme avec le launcher sur tel est fixé
- ajout de discription et de tutoriel dans le launcher
- zoom et dezoom ajouté


---
## 📄 Licence

Projet 1 dévlopeur — fichier HTML autoportant, aucune dépendance.

| Indicateur | dévlopeurs |
|------------|----------------------|
| **dévlopeur en chef** | xxtag01 |
| **dévlopeur en second**| XXDad01
