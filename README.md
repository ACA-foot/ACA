# Site de statistiques — ACA

Site statique (une seule page `index.html`) qui affiche les statistiques de
toutes les catégories du club (U18, U14-U15, U10-U11), à partir de fichiers
Excel que vous mettez à jour vous-même. Personne d'autre ne peut modifier quoi
que ce soit : les visiteurs ne font que consulter.

## 1. Fichiers à héberger ensemble

Ces fichiers doivent toujours se trouver **au même endroit**, avec **ces noms
exacts** :

| Fichier | Contenu |
|---|---|
| `index.html` | La page elle-même (le code du site) |
| `accueil.jpg` | Bannière affichée sur la page d'accueil |
| `Effectif.xlsx` | Effectif de **toutes** les catégories (U18 Éq.1, U18 Éq.2, U14-15, U10-11) — fichier unique |
| `entrainements.xlsx` | Fichier maître des présences aux entraînements — **toutes** les catégories |
| `data_equipe1.xlsx` | Classeur de suivi de saison — U18 Équipe 1 |
| `data_equipe2.xlsx` | Classeur de suivi de saison — U18 Équipe 2 |
| `data_U14-15.xlsx` | Classeur de suivi de saison — U14-U15 (U15-D2 et U15-D3) |
| `data_U10-11.xlsx` | Classeur de suivi de saison — U10-U11 (U11-D2, U11-D3-A, U11-D3-B) |
| `FeuilleMatchA4-Equipe1.pdf` | Feuille de match imprimable — U18 Équipe 1 |
| `FeuilleMatchA4-Equipe2.pdf` | Feuille de match imprimable — U18 Équipe 2 |
| `FeuilleMatchA4-U14-15.pdf` | Feuille de match imprimable — U14-U15 |
| `FeuilleMatchA4-U10-11.pdf` | Feuille de match imprimable — U10-U11 |

Si l'un des fichiers de données est absent, seule la partie du site qui en
dépend affiche un message d'erreur — le reste continue de fonctionner
normalement.

## 2. Mise en ligne (à faire une seule fois)

1. Créez un compte gratuit sur https://github.com si vous n'en avez pas.
2. Cliquez sur **New** (nouveau dépôt).
   - Nom : par exemple `ACA`
   - Cochez **Public**
   - **Create repository**
3. **Add file > Upload files**, glissez-déposez tous les fichiers listés
   ci-dessus, puis **Commit changes**.
4. **Settings > Pages** (menu de gauche) → sous **Branch**, choisissez `main` →
   **Save**.
5. Patientez 1-2 minutes, rechargez la page : l'adresse de votre site apparaît
   en haut (ex. `https://votre-pseudo.github.io/ACA/`).
6. Partagez cette adresse au club. Elle ne change plus jamais, même après de
   futures mises à jour.

## 3. Mettre à jour les stats d'une équipe (après chaque match)

1. Renseignez votre classeur Excel comme d'habitude.
   - **U18** (Équipe 1 / Équipe 2) : onglets Matchs, Buts, Cartons,
     Convocations & Temps de jeu, Changements, Gardien.
   - **U14-15 / U10-11** : onglets Matchs (avec la colonne "Équipe" pour
     préciser U15-D2/U15-D3 ou U11-D2/U11-D3-A/U11-D3-B), Convocations, Buts,
     Cartons, Gardien. Pas de temps de jeu ni de "Changements" pour ces deux
     catégories — c'est volontairement plus simple.
2. Sur GitHub, ouvrez le fichier `data_...xlsx` concerné, cliquez sur l'icône
   crayon (ou supprimez puis **Add file > Upload files** pour le remettre), et
   uploadez votre fichier à jour **sous ce même nom exact**.
3. **Commit changes**.
4. La page se met à jour automatiquement (rechargez-la après une minute).

**Important :** ne renommez jamais ces fichiers — le site les cherche par leur
nom exact.

## 4. Mettre à jour les présences aux entraînements

Le fichier `entrainements.xlsx` est un fichier **maître qui s'enrichit chaque
semaine** (il garde tout l'historique de la saison, pour les 4 catégories à
la fois), contrairement aux exports bruts de l'outil de gestion (TeamSnap ou
autre) qui ne couvrent que quelques dates à la fois.

**Marche à suivre :**
1. Téléchargez le nouvel export depuis votre outil — un seul export couvrant
   toutes les catégories suffit (U18-1, U18-2, U10-U11, U14-15).
2. Envoyez ce fichier brut à Claude (dans une conversation du projet), en
   demandant de le fusionner dans le fichier maître.
3. Claude vous renvoie `entrainements.xlsx` mis à jour, prêt à remplacer
   l'ancien sur GitHub (même procédure qu'à la section 3).
4. Pensez aussi à **mettre à jour la copie de `entrainements.xlsx` dans les
   fichiers du projet Claude**, pour que la prochaine fusion reparte de la
   bonne version.

## 5. Ajouter, retirer ou transférer un joueur

Toujours commencer par mettre à jour **`Effectif.xlsx`** (les 4 colonnes : U18
Éq.1, U18 Éq.2, U14-15, U10-11), puis prévenir Claude — un changement
d'effectif nécessite une petite modification du classeur Excel de l'équipe
concernée (au-delà d'un simple remplacement de fichier) pour que les formules
et l'historique déjà saisi restent cohérents, notamment en cas de transfert
d'un joueur en cours de saison entre Équipe 1 et Équipe 2.

## 6. Ce qu'affiche le site

- **Accueil** — bannière du club et liens de téléchargement des 4 feuilles de
  match imprimables.
- **U18** — vue d'ensemble combinant Équipe 1 et Équipe 2 : tableau
  "Utilisation joueurs" (matchs, buts, cartons, % de convocation par équipe,
  séances et % de présence aux entraînements — colonnes "Matchs" et
  "Entraînement" bien distinguées visuellement).
- **U18 Équipe 1** / **U18 Équipe 2** — vue complète par équipe, avec 3
  onglets :
  - **Joueurs** : tableau d'utilisation joueurs (triable, filtrable),
    gardiens, top buteurs, top passeurs, suivi des absences par motif, fiche
    détaillée par joueur.
  - **Matchs** : bilan de la saison, liste des matchs, détail par match avec
    composition, chronologie interactive (joueurs sur le terrain, buts,
    changements), tableaux détaillés.
  - **Entraînement** : grille de présence par séance et taux de participation.
- **U14-U15** / **U10-U11** — mêmes 3 onglets dans une version simplifiée
  (sans temps de jeu) :
  - **Joueurs** : matchs joués, buts, cartons (U14-15 seulement), % de
    convocation global et par équipe interne, présence aux entraînements.
  - **Matchs** : liste des matchs (plusieurs par week-end, un par équipe
    interne), détail par match (composition, buts, cartons, gardien).
  - **Entraînement** : grille de présence par séance.

## 7. Qui peut modifier quoi ?

- Les membres du club qui ont l'adresse du site peuvent uniquement
  **consulter**.
- Seule la personne ayant accès au dépôt GitHub peut mettre à jour les
  fichiers et donc changer ce qui s'affiche.

---
*Conception : P. Meyer — dernière mise à jour de ce document : voir la date en
bas de la page du site elle-même.*
