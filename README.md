🏙️ OMEGA CITY — v1.21.1
Un jeu de construction de ville (city-builder) jouable entièrement dans le navigateur, sans installation ni dépendance externe. Un seul fichier HTML suffit.

🚀 Lancement
Ouvre simplement omega_1_21_1.html dans n'importe quel navigateur moderne (Chrome, Firefox, Edge, Safari).
Aucun serveur, aucune installation requise.

🎮 Modes de jeu
ModeArgent de départParticularitéNormal2 000 €Économie stricte, arbre technologique actifDifficile500 €Entretien +50 %, exports d'énergie −50 %, taxes −20 %, clics −50 %CréatifInfiniSandbox libre, toutes les technologies débloquées, pas de coûts

🖥️ Interface
┌─────────────────────────────────────────────────────────┐
│                      BARRE DU HAUT                      │
│          (argent · population · énergie · science)      │
├──────────────┬──────────────────────────┬───────────────┤
│  PANNEAU     │                          │   PANNEAU     │
│  GAUCHE      │       GRILLE DE JEU      │   DROIT       │
│              │        (canvas)          │               │
│ · Bouton     │                          │ · Finances    │
│   cliqueur   │                          │ · Satisfaction│
│ · Menu de    │                          │ · Emplois     │
│   bâtiments  │                          │ · Pollution   │
├──────────────┤                          │               │
│              ├──────────────────────────┤               │
│              │     JOURNAL (logs)       │               │
└──────────────┴──────────────────────────┴───────────────┘

Les séparateurs entre panneaux sont redimensionnables à la souris ou au toucher.
Clic gauche sur la grille : poser un bâtiment.
Clic droit + glisser : déplacer la caméra.
Survol d'une tuile : affiche un tooltip avec l'état du bâtiment.


🏗️ Bâtiments
Infrastructures
IcôneNomCoûtEffet🛣️Route50 €Connexion des tuiles🧨DétruireGratuitSupprime un bâtiment
Habitations (génèrent population et taxes)
IcôneNomCoûtPopTaxes/s🏠Cabane200 €6900 €🏡Pavillon500 €161 200 €🏢Immeuble1 200 €2153 500 €
Production d'énergie
IcôneNomCoûtProductionTechnologie requise🔥Centrale Charbon1 000 €80—🌀Éolienne1 500 €700Écologie☀️Solaire3 500 €300Écologie💦Turbine à vagues3 000 €550Océan☢️Nucléaire10 000 €500Usinage⚛️Accélérateur de particules1 000 000 000 €1 000 000Militaire Avancé
Services & Bonheur
IcôneNomCoûtEffet🏫École4 000 €Science +3/s🌳Parc1 000 €Bonheur +5⚽Stade8 000 €Bonheur +50👮Police3 000 €Bonheur +10🧬Centre de Recherche5 000 €Science +30/s🧪Super Labo15 000 €Science +70/s
Industrie & Finance
IcôneNomCoûtTaxes/s🏧Petite banque10 000 €100 000 €💳Banque100 000 €1 000 000 €💶Banque municipale150 000 €1 500 000 €💻🏭Usine de PC28 000 €10 000 €👽Zone 511 000 000 €100 000 €
Militaire (nécessite tech Militaire)
IcôneNomCoût🔈Petite base militaire7 000 €🔉Base militaire14 000 €🔊Grande base militaire28 000 €🛫Aérodrome28 000 €🚫Système antidrone15 000 €
Nature (nécessite tech « La route vers la nature »)
IcôneNomEffet pollution🌊Océan—🏖️Étang−10🌅Mer−30🌳Forêt−15

🔬 Arbre Technologique
Les technologies se débloquent avec des points de science (🧪), générés par les écoles et labos.
Départ
├── Urbanisme (100 Sc)
│   ├── Culture (125 Sc)
│   ├── Sécurité (300 Sc)
│   │   └── Militaire (1 000 Sc)
│   │       └── Militaire Avancé (5 000 Sc)
│   └── Usinage (2 500 Sc)
│       └── Gamming (50 Sc)
│           └── Restauration (1 000 Sc)
└── La route vers la nature (25 Sc)
    └── Écologie (200 Sc)
        └── Physique (600 Sc)

📊 Économie
Le revenu par seconde est calculé ainsi :
Revenu net = Taxes des bâtiments + Export d'énergie − Entretien

Export d'énergie : chaque unité d'énergie excédentaire rapporte 3 €/s (désactivé en mode Créatif).
Entretien : chaque bâtiment a un coût fixe par seconde.
Bouton cliqueur : génère un revenu immédiat basé sur 50 + (population × 2) + (science × 1).

Indicateurs surveillés
IndicateurImpact négatif si...Satisfaction< 40 % (rouge) — chute si pollution élevée ou chômage > 70 %Emplois< 30 % de la population → −15 de satisfactionPollutionChaque unité retire 2 points de satisfactionÉnergieBâtiment sans courant = inactif (bordure rouge)TravailleursBâtiment sans main-d'œuvre = inactif (bordure orange)

⚙️ Architecture technique
Le jeu est entièrement contenu dans un seul fichier HTML (~1 300 lignes) organisé en modules JavaScript :
ModuleRôleDBBase de données des bâtiments et technologiesStateÉtat global du jeu (argent, grille, mode, etc.)GameBoucle principale, démarrage, clicsGridRendu canvas, gestion de la caméra, placementSimulationCalcul population, énergie, taxes, pollutionUIMise à jour de l'interface, menus, arbre techLoggerJournal d'événements en bas de l'écran
La grille est de 60 × 60 tuiles (32 px chacune). La propagation de l'électricité utilise un algorithme BFS depuis les sources d'énergie.

📝 Notes de version 1.21.1

Ajout du système de taxes sur les habitations et bâtiments générateurs.
Refonte du calcul du revenu net : Taxes + Exports − Entretien.
Nouveau bâtiment : turbine à vagues (nécessite la technologie Océan).
Bâtiments militaires complets (petite/moyenne/grande base, aérodrome, antidrone).
Banques avec taxes massives pour les fins de partie.
Interface redimensionnable compatible mobile (touch).


📄 Licence
Projet solo — fichier HTML autoportant, aucune dépendance.
