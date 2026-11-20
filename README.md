# Dossier patient — Urgences

Application web monopage autonome (un seul fichier HTML/CSS/JS) destinée au suivi rapide des dossiers patients en médecine d'urgence, compatible PC, téléphone et tablette. L'interface applique les spécifications ergonomiques et design Material Design 3 et fonctionne intégralement hors ligne, sans base de données externe ni installation.

## Avertissement

Cet outil est une aide à l'organisation personnelle et à la prise de notes pendant la garde. Il remplace simplement le bloc-notes utilisé habituellement; mais pas un dossier patient informatisé (DPI) certifié. Les données étant stockées localement ou dans des fichiers `.json` gérés par l'utilisateur, il appartient à chaque praticien de respecter la confidentialité des données médicales (RGPD), d'anonymiser les saisies si nécessaire et de purger les dossiers en fin de vacation.
Cet outil n'est pas moins sécurisé que l'usage du bloc-notes, mais ne l'est pas non-plus davantage. Il permet simplement une meilleure organisation de la prise de notes.
La synchronisation automatique du fichier .JSON contenant les données patient permet un accès depuis les différents ordinateurs du services, tant qu'il y a un accès au même fichier HTML. Une synchornisation manuelle est nécessaire par mesure de sécurité quand une connexion est effectuée sur un nouveau pc, afin de ne pas accidentellement écraser une sauvegarde en cours.

## Fonctionnalités

### Gestion de file active et tri
* **Repérage spatial et gravité** : attribution d'un box ou secteur et d'une pastille de tri à 5 niveaux (Blanc, Vert, Orange, Rouge, Noir) avec double contour haute visibilité.
* **Filtrage instantané** : recherche textuelle (box, nom, âge, motif) et filtres rapides par statut (**Tous**, **Présents**, **Attente**, **Sortis**).
* **Tri multi-critères** : classement ascendant ou descendant par heure d'arrivée, niveau de gravité, numéro de box ou nom de famille.

### Dossier clinique et suivi paraclinique
* **Suivi des examens** : puces interactives à trois états (neutre, en attente, vu/fait) pour la **Biologie**, l'**ECG**, l'**Imagerie** et les **Avis**.
* **Navigation par onglets** : accès direct aux 12 rubriques cliniques (*Motif, Antécédents, Allergies, Mode de vie, Traitement, Anamnèse, Examen, Bilan, Évolution, Conclusion, CAT, Sortie*) ainsi qu'à une **Vue globale** éditable.
* **Constantes vitales** : grille dédiée en tête de l'onglet *Examen clinique* (PA, FC, SpO2, T°, FR, HGT, EVA).
* **Traçabilité des allergies** : alerte visuelle dès la saisie d'une allergie ou validation explicite via la case *Aucune allergie*.

### Ergonomie, impression et sauvegarde JSON
* **Thèmes d'affichage** : modes **Clair**, **Sombre** et **AMOLED** (noir pur).
* **Export et impression** : copie de l'observation structurée dans le presse-papiers, impression d'un dossier individuel ou de l'ensemble de la relève (mise en page noir et blanc dédiée).
* **Persistance et portabilité JSON** : sauvegarde automatique dans le `localStorage`, export/import manuel au format `.json`, mode **Autosave JSON** (téléchargement automatique d'une sauvegarde `urgences_patients_autosave.json` à chaque modification)
* **Suppression de dossier** avec annulation possible pendant 7 secondes.
* **Possibilité de barrer un patient** après avoir traité le cas.

## Installation et utilisation

### Utilisation locale (poste unique)
1. Télécharger le fichier HTML depuis ce dépôt.
2. Ouvrir le fichier directement dans un navigateur web récent (Chrome, Edge, Brave ; Firefox et Safari n'ont pas été testé pour la sauvegarde automatique et ne semble pas fonctionner).

### Accès et partage sur réseau local (LAN)
L'architecture sans dépendances et le format d'échange `.json` permettent d'utiliser l'outil sur plusieurs postes ou terminaux mobiles connectés au même réseau local :

* **Via un dossier réseau partagé (SMB / lecteur réseau)** : placer le fichier HTML et les sauvegardes `.json` dans un répertoire partagé du réseau local. N'importe quel poste autorisé peut ouvrir l'application et charger l'état le plus récent via le bouton **Import**, puis le mettre à jour via **Export** ou **Autosave JSON**.
* **Via un micro-serveur HTTP local (multi-appareils : PC, tablette, smartphone)** : lancer un serveur web léger dans le dossier contenant le fichier HTML :
  ```bash
  python -m http.server 8000
