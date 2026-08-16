# Visualiseur 3D OpenDrone 3"

Ce projet autonome permet de visualiser en 3D temps réel le drone **OpenDrone 3"** du site officiel [opendrone.be](https://opendrone.be) avec un rendu PBR haute fidélité identique à l'original.

---

## Fonctionnalités intégrées

- **Moteur 3D Three.js PBR avancé** : Rendu physique avec PMREM (RoomEnvironment), ACES Filmic Tone Mapping et correction gamma sRGB vers espace linéaire pour les couleurs CAD Onshape.
- **Profils de matériaux sur-mesure** : Carbone T700, aluminium CNC, vernis PCB vert soldermask, sérigraphie silkscreen, connecteurs et pistes dorés ENIG, cloche de moteur anodisée, TPU, etc.
- **Éclairage 3 points Studio + Bounce** : Key Light (#e69728), Fill Light (#e5f7de), Rim Light (#cfe2ff) et Bounce (#7d7417).
- **Navigation par étapes (Timeline Walkthrough)** :
  1. Vue globale du drone 3" assemblé
  2. Contrôleur de vol OpenFC-Lite-Mini (RP2354B)
  3. Variateur ESC 4-en-1 OpenESC (AM32)
  4. Récepteur radio OpenRX-Mono (ELRS)
  5. Propulsion : moteurs brushless 1604 et hélices tri-pales rotatives
  6. Châssis carbone T700 et berceau vidéo VTX démontable
- **Arbre d'assemblage simplifié** : 29 pièces principales seulement, regroupées en 6 catégories (Structure carbone, Propulsion, Électronique, Vidéo & FPV, Pièces TPU, Visserie & connectique). Chaque ligne regroupe la totalité des corps CAO de la pièce : masquer « Moteur avant droit » masque le moteur entier, masquer « OpenFC-Lite » masque les 700 corps de la carte. Cases à cocher par pièce et par catégorie, boutons Tout afficher / Tout masquer, filtre texte, et sélection synchronisée avec le clic dans la vue 3D.
- **Vue éclatée interactive** : Slider pour écarter les pièces en 3D dans l'espace, chaque pièce restant solidaire.
- **Transitions animées** : Le passage entre « Mise à plat » et « Assembler » se joue en cascade — les pièces partent en décalé (structure d'abord au montage, extérieur d'abord au démontage) avec une interpolation adoucie, pendant que la caméra vole jusqu'au nouveau cadrage.
- **Montage pas à pas** : Le mode « Pièce par Pièce » affiche une barre en bas de l'écran avec flèches Précédent / Suivant (également pilotable aux flèches du clavier) ; chaque pièce ajoutée vient se poser depuis l'extérieur et son nom s'affiche dans l'encart.
- **ViewCube CAO** : Un clic sur une face du cube en haut à droite oriente la vue sur l'axe correspondant du drone (Avant = côté caméra FPV), en vol animé et sans changer le zoom ; le cube reste orientable à la souris.
- **Fond du plan de travail** : Origine (fond du site), Bleu foncé, Gris ou Blanc.
- **Inspecteur de composants (Raycasting 3D)** : Cliquez sur n'importe quel composant pour afficher son nom, son type de matériau, son nombre de polygones et ses dimensions exactes en millimètres.
- **Profils d'éclairage** : Studio, Dramatique, Doux, Technique.
- **Contrôles d'animation** : Vitesse de rotation des hélices, auto-rotation de caméra (elle repart de la vue courante, sans saut de distance ni d'élévation), mode filaire (Wireframe), plein écran.
- **Commander / Télécharger les pièces** : Bouton en bas à droite ouvrant le choix du kit — drone entier, châssis carbone, TPU, propulsion ou électronique — avec la liste des pièces et leur nombre, calculés depuis l'arbre d'assemblage. Le STL binaire est généré à la volée depuis le modèle affiché (pièces remises à leur position d'assemblage) ; le STEP paramétrique, absent du visualiseur qui ne contient que des maillages, renvoie vers opendrone.be, tout comme la commande.
- **100% autonome et hors-ligne** : Tous les modèles GLB et les bibliothèques Three.js sont inclus localement.

---

## Comment lancer le visualiseur

### Méthode 1 (Recommandée sous Windows) :
Double-cliquez simplement sur :
```
lancer_visualiseur.bat
```
ou exécutez dans PowerShell :
```powershell
.\lancer_visualiseur.ps1
```

### Méthode 2 (Ligne de commande) :
Dans le dossier du projet :
```bash
python -m http.server 8000
```
Puis ouvrez votre navigateur à l'adresse : **[http://localhost:8000](http://localhost:8000)**

---

## Structure des dossiers

```
opendrone-3d-viewer/
├── index.html                # Page principale de visualisation 3D
├── lancer_visualiseur.bat    # Script de lancement 1-clic
├── lancer_visualiseur.ps1    # Script PowerShell
├── README.md                 # Documentation
├── libs/                     # Three.js et addons téléchargés localement
└── models/
    └── od3/                  # Modèles 3D OpenDrone 3" (frame, drive, video, OpenFC, 4in1, OpenRX)
```
