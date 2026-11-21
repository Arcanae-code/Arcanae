# Arcanae

Site de la structure Esport Overwatch **Arcanae**.

Site statique : aucun serveur, aucune base de données, aucune dépendance.

## Fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | Le site entier : mise en forme, code, et une copie de secours des données. Le logo papillon y est intégré. |
| `data.json` | **Tout le contenu modifiable** : équipes, couleurs, joueurs, direction, liens. C'est le seul fichier à remplacer pour mettre le site à jour. |
| `logo-tempest.png` | Logo de l'équipe Tempest. |
| `logo-arcanae.png` | Logo de la structure, pour l'icône d'onglet et l'aperçu de partage. |

Les autres logos d'équipe s'ajoutent depuis l'éditeur, sans toucher aux fichiers.

## Modifier le site

1. Ouvrir le site en ajoutant `?admin` à la fin de l'URL :
   `https://pcou-code.github.io/Arcanae/?admin`
2. Cliquer **Mode édition** en haut à droite.
3. Modifier, puis cliquer **Télécharger data.json**.
4. Sur GitHub : *Add file → Upload files*, déposer le nouveau `data.json`, *Commit changes*.
5. Une minute plus tard, tout le monde voit la nouvelle version.

Le paramètre `?admin` ne protège rien, il cache seulement le bouton aux visiteurs.
Publier reste impossible sans accès au dépôt.

### Ce qui est modifiable depuis l'éditeur

Sur l'accueil : ajouter, renommer, recolorer, réordonner ou supprimer une équipe ;
la direction (noms et intitulés) ; les liens (plateforme, nom affiché, URL) ; la phrase d'accroche.

Sur une page d'équipe : ajouter et supprimer des joueurs, changer leur rôle, leur pseudo,
leurs héros, désigner un capitaine, déplacer un joueur vers une autre équipe,
charger le logo de l'équipe et choisir un fond clair ou sombre derrière lui.

## Structure de data.json

```json
{
  "org": {
    "tagline": "Structure Overwatch…",
    "heroesDir": "heroes/",
    "staff": [{ "id": "s1", "name": "Nexola", "title": "CEO" }],
    "links": [{ "id": "l1", "platform": "tiktok", "label": "TikTok", "url": "https://…" }]
  },
  "teams": [{
    "id": "tempest",
    "name": "Tempest",
    "color": "#CFE6FF",
    "colorLabel": "bleu glacé",
    "logo": "logo-tempest.png",
    "lightCrest": false,
    "players": [{
      "id": "p9",
      "pseudo": "Pcou",
      "role": "Tank",
      "main": "reinhardt",
      "heroes": "Reinhardt, Sigma",
      "captain": false,
      "links": { "twitch": "", "discord": "", "instagram": "", "tiktok": "", "x": "" }
    }]
  }]
}
```

### Les champs d'un joueur

- `role` : Tank, Hitscan, Flex DPS, Main Support, Flex Support, Remplaçant, En essai, Coach, Manager.
  Le pictogramme se déduit du rôle : bouclier pour les tanks, réticule pour les DPS, croix pour les supports.
  **Coach et Manager sont affichés à part**, sous un bloc « Encadrement », en bas de la page d'équipe.
- `main` : le personnage principal, affiché en grand sur la fiche du joueur.
  Écrire le nom du fichier sans le dossier : `"reinhardt"` ou `"reinhardt.png"`, les deux marchent.
  Le site va le chercher dans le dossier indiqué par `heroesDir`, donc `heroes/reinhardt.png`.
- `heroes` : les héros joués, séparés par des virgules. Affichage en texte seulement.
- `captain` : `true` pose l'étiquette « capitaine » à côté du pseudo. Sans guillemets.
- `links` : les cinq réseaux du joueur. **Un réseau laissé vide n'apparaît pas du tout** —
  aucun bouton grisé, aucune mention. Seuls les renseignés sont affichés.

### Les images de personnages

Déposer les PNG dans un dossier `heroes` à la racine du dépôt, nommés `nom.png` en minuscules
et sans accent : `heroes/tracer.png`, `heroes/lucio.png`, `heroes/wrecking-ball.png`.

Pour créer le dossier sur GitHub : *Add file → Upload files*, puis glisser le **dossier** `heroes`
entier (et non les fichiers un par un, contrairement aux fichiers de la racine).

Pour changer d'emplacement, modifier `heroesDir` dans `org`. La valeur doit finir par `/`.
La laisser vide met les images à la racine du dépôt.

### Les autres champs

- `platform` d'un lien de structure : tiktok, instagram, twitch, discord, youtube, x,
  ou site pour une icône générique.
- `logo` : un nom de fichier du dépôt, ou une image encodée en `data:image/png;base64,…`
  (ce que produit l'éditeur quand on charge un logo).
- `crestBg` : couleur de fond derrière le logo d'une équipe, par exemple `"#5A6B84"`.
  Absent ou vide, le logo est posé directement sur le fond du site.
- `id` : n'importe quelle chaîne unique.

## Naviguer dans le site

Accueil → une équipe → un joueur. Chaque ligne de roster est cliquable et mène à la fiche
du joueur : son personnage en grand, ses héros, et ses réseaux.

L'adresse d'une fiche est de la forme `#tempest--p9`, donc chaque joueur a son lien partageable.

## Nom de domaine

*Settings → Pages → Custom domain*. Le HTTPS est fourni gratuitement.
