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
- **Mise à plat par famille** : Sur le plateau, les pièces sont rangées comme dans l'arbre d'assemblage — les 4 moteurs en bloc 2x2, les 4 hélices de même, puis chaque catégorie à la suite. Les familles ne sont jamais coupées, et deux catégories courtes partagent une bande pour garder le plateau compact.
- **Thèmes prédéfinis** : Bicolores OpenDrone (Bleu/Jaune, Bleu/Blanc, Bleu/Noir, Vert/Violet) construits autour du bleu roi, et signatures d'origine (Cyberpunk, Sunset, Stealth, Gold). Chaque catégorie de pièces garde par ailleurs sa palette de 11 nuances.
- **Transitions animées** : Le passage entre « Mise à plat » et « Assembler » se joue en cascade — les pièces partent en décalé (structure d'abord au montage, extérieur d'abord au démontage) avec une interpolation adoucie, pendant que la caméra vole jusqu'au nouveau cadrage.
- **Montage pas à pas** : Le mode « Pièce par Pièce » affiche une barre en bas de l'écran avec flèches Précédent / Suivant (également pilotable aux flèches du clavier) ; chaque pièce ajoutée vient se poser depuis l'extérieur et son nom s'affiche dans l'encart.
- **Sélecteur de vue (bas à gauche)** : Une croix de type pavé directionnel — Dessus, Dessous, Gauche et Droite sur la croix, Recentrer au centre, les deux isométries juste en dessous. Les vues suivent les axes propres du drone et réutilisent le même vol de caméra que le ViewCube, en conservant le zoom courant. Repliable en une pastille, et l'arbre d'assemblage ajuste sa hauteur pour ne jamais le recouvrir.
- **ViewCube CAO** : Un clic sur une face du cube en haut à droite oriente la vue sur l'axe correspondant du drone (Avant = côté caméra FPV), en vol animé et sans changer le zoom ; le cube reste orientable à la souris.
- **Fond du plan de travail** : Origine (fond du site), Bleu foncé, Gris ou Blanc.
- **Arêtes surlignées** : Case à cocher dans Affichage qui superpose les contours CAO des pièces. Les contours sont extraits à la première activation, étalés sur plusieurs images pour ne jamais figer l'interface, puis conservés ; les pastilles, sérigraphies et composants CMS des cartes en sont exclus (93 % des triangles pour un résultat qui ne serait que du bruit), tout comme les quelques maillages courbes les plus lourds.
- **Inspecteur de composants (Raycasting 3D)** : Cliquez sur n'importe quel composant pour afficher son nom, son type de matériau, son nombre de polygones et ses dimensions exactes en millimètres.
- **Profils d'éclairage** : Studio, Dramatique, Doux, Technique.
- **Contrôles d'animation** : Vitesse de rotation des hélices, auto-rotation de caméra (elle repart de la vue courante, sans saut de distance ni d'élévation), mode filaire (Wireframe), plein écran.
- **Câblage 3D** : Le faisceau complet est construit en code (les GLB ne contiennent que les embases posées sur les cartes) — 12 phases moteur, **chacune un fil à part entière** posée sur **sa propre pastille de cuivre**, repérée dans le GLB et non inventée : six pastilles carrées par flanc de l'ESC, trois par moteur, espacées de 3,5 mm pour une bille d'étain de 1,5 mm — une bille ne peut jamais chevaucher deux plots, nappe JST-SH 8 broches ESC→FC, nappe 6 broches FC→VTX, CRSF 4 fils du récepteur, coaxiaux d'antennes, nappe caméra, et la queue batterie rouge/noir. Les fils sont ancrés aux pièces : ils suivent l'éclatement, la mise à plat et le pas-à-pas **en restant connectés aux deux extrémités**. Embouts modélisés au plus près du montage réel : **une vraie fiche là où il y en a une** (JST-SH 4/6/8 broches sur les nappes, u.FL sur les coaxiaux), une **ferrule étamée** là où le fil part directement au fer (phases moteur, queue batterie). Le XT30 mâle/femelle est **enfilé sur le câble de batterie** et glisse avec lui — rien de jaune ne traîne sur la carte, l'ESC ne porte que ses plots soudés. Chaque embout sert aussi de poignée de saisie. Condensateur low-ESR et billes de soudure complètent l'ensemble : l'étain n'apparaît qu'une fois le fil réellement posé sur son plot, exactement au même point que sa pointe, et la bille **repose sur** la face cuivrée : sa base touche le plan du cuivre, elle ne le traverse pas. Le plan de pose est la face du PCB relevée dans le modèle, pas le sommet de la boîte englobante — celui-ci est 6 mm plus haut, à hauteur des connecteurs. Interrupteur « Câblage » dans Affichage.
- **Batterie** : Pack LiPo 4S 850 mAh construit d'après le visualiseur TinyHoop MK1 — wrap noir mat à arêtes arrondies, étiquette imprimée sur le dessus seulement, feuille d'aluminium apparente aux deux bouts — posé sur la plaque supérieure dans l'axe du drone, avec sa queue rouge/noir et son XT30. Pièce à part entière de l'arbre (catégorie Batterie), donc masquable, exportable et posée sur le plateau comme les autres.
- **Établi de câblage** : À l'ouverture du mode, tout ce qui ne sert pas au câblage disparaît — il ne reste que l'électronique, la vidéo, la batterie et les quatre moteurs (les soudures de phases s'y rattachent) — et la caméra vient **cadrer serré le stack FC/ESC/RX**. Sur les étapes qui se soudent sur l'ESC — phases, condensateur, XT30 — le FC et le récepteur **s'écartent en hauteur et vers l'avant** pour dégager la face cuivrée : c'est aussi l'ordre de montage réel, on soude l'ESC à nu avant d'empiler. Ils reviennent en place dès l'étape suivante. La batterie se déporte à gauche du drone le temps du mode : posée sur la plaque haute elle masquerait exactement les cartes qu'on vient regarder ; elle retrouve sa place à la sortie. Les nappes et câbles libres sont alors **déposés à plat sur un tapis d'établi**, à côté du drone, une voie par câble dans l'ordre des étapes. Les 12 phases, elles, **sortent déjà soudées aux moteurs** : seul leur bout ESC est libre, et il attend à plat juste à côté de son plot, pointé dessus. À la sortie du mode, tout revient d'un coup : pièces réaffichées et faisceau rebranché.
- **Câbles manipulables** : En mode câblage, un clic maintenu sur un câble le déplace dans le plan horizontal. Saisir près d'un bout (ferrule ou premier quart du fil) déplace **cette extrémité seule** ; saisir au milieu déplace le câble entier s'il est rangé, ou tire son point de mou s'il est déjà branché — sans jamais décrocher les deux bouts. Un bout déjà soudé ne se décolle pas : la saisie bascule sur l'autre extrémité. Surtout, **lâcher un bout à moins de 7 mm de son point d'arrivée le raccorde** — le clipsage se joue, l'étain apparaît, et l'étape se valide toute seule quand ses derniers fils sont posés. L'orbite est suspendue pendant le glissement, et la saisie d'un fil prime sur la sélection de pièce sans la perturber ailleurs.
- **Mode Câblage (WIRING)** : Parcours interactif en 10 étapes, du choix props-in / props-out jusqu'au test final. Chaque étape porte sa consigne, un indice dépliable et une cible surlignée en 3D par un anneau pulsant, qui **désigne le prochain fil à poser** et se déplace au fur et à mesure — sur les douze phases c'est lui qui guide. Les soudures se font en maintenant le clic (une soudure trop brève est refusée comme soudure froide) ; « Brancher » **joue le clipsage** — le câble quitte l'établi et vient rejoindre ses connecteurs en vol adouci, puis le boîtier marque un à-coup d'encliquetage. Les étapes de soudure raccordent leurs fils de la même façon en fin de maintien. Le brochage affiché est celui des cartes réelles, relevé sur les dépôts incutec-hw : ESC→FC `+BATT · GND · CURR · NC · M1 · M2 · M3 · M4`, VTX `+10V · GND · DIGITAL_TX · DIGITAL_RX · GND · SBUS`, récepteur CRSF. Le sens de rotation CW/CCW découle de l'ordre des phases et suit la table Betaflight. Un test final vérifie l'ensemble : tout bon donne des cotillons, une faute donne de la fumée à la jonction fautive avec son diagnostic. Un dépliant permet de provoquer volontairement les trois fautes classiques (XT30 inversé, condensateur à l'envers, phases inversées) pour voir ce que le test détecte, et un second liste les pièces suggérées.
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
