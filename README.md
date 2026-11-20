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
    "staff": [{ "id": "s1", "name": "Nexola", "title": "CEO" }],
    "links": [{ "id": "l1", "platform": "tiktok", "label": "TikTok", "url": "https://…" }]
  },
  "teams": [{
    "id": "tempest",
    "name": "Tempest",
    "color": "#CFE6FF",
    "colorLabel": "bleu glacé",
    "logo": "logo-tempest.png",
    "lightCrest": true,
    "players": [
      { "id": "p9", "pseudo": "Pcou", "role": "Tank", "heroes": "Reinhardt, Sigma", "captain": false }
    ]
  }]
}
```

- `role` : Tank, Hitscan, Flex DPS, Main Support, Flex Support, Remplaçant, En essai, Coach, Manager.
  Le pictogramme se déduit du rôle : bouclier pour les tanks, réticule pour les DPS, croix pour les supports.
- `platform` : tiktok, instagram, twitch, discord, youtube, x, ou site pour une icône générique.
- `logo` : un nom de fichier du dépôt, ou une image encodée en `data:image/png;base64,…`
  (ce que produit l'éditeur quand on charge un logo).
- `lightCrest` : `true` pose le logo sur une plaque claire — nécessaire pour un logo
  aux détails sombres. `false` le laisse sur le fond sombre du site.
- `id` : n'importe quelle chaîne unique.

La copie de secours intégrée à `index.html` ne sert que si `data.json` est introuvable.
Tant que `data.json` est en place, c'est lui qui fait foi.

## Nom de domaine

*Settings → Pages → Custom domain*. Le HTTPS est fourni gratuitement.
