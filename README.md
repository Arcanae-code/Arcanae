# Arcanae

Site de la structure Esport Overwatch **Arcanae** (Lunaris, Solaris, Stellaris, Tempest).

Site statique : aucun serveur, aucune base de données, aucune dépendance à installer.

## Fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | Le site entier (structure, style, code). Le logo du papillon y est intégré. |
| `data.json` | **Les données modifiables** : CEO, liens des réseaux, rosters, logos d'équipe. |
| `logo-arcanae.png` | Le logo, utilisé pour l'icône de l'onglet et l'aperçu quand on partage le lien. |

## Mettre en ligne (GitHub Pages)

1. Créer un dépôt **public** nommé `Arcanae`.
2. *Add file → Upload files*, déposer les trois fichiers, *Commit changes*.
3. *Settings → Pages → Source: Deploy from a branch → Branch: `main` / `/ (root)` → Save*.
4. Au bout d'une minute, le site est sur `https://<utilisateur>.github.io/Arcanae/`.

## Modifier les rosters

Deux méthodes, au choix.

### Avec l'éditeur intégré (recommandé)

1. Ouvrir le site en ajoutant `?admin` à la fin de l'URL :
   `https://<utilisateur>.github.io/arcanae/?admin`
2. Cliquer **Mode édition** en haut à droite. On peut alors :
   - modifier rôle, pseudo et héros de chaque joueur ;
   - déplacer un joueur vers une autre équipe (menu déroulant à droite de sa ligne) ;
   - ajouter ou supprimer un joueur ;
   - choisir le logo d'une équipe depuis son ordinateur ;
   - sur l'accueil, changer les noms des CEO et les liens TikTok / Instagram / Twitch / Discord.
3. Les changements restent sur l'appareil tant qu'ils ne sont pas publiés. Cliquer
   **Télécharger data.json**, puis remplacer `data.json` dans le dépôt
   (*Add file → Upload files*, déposer le nouveau fichier, *Commit changes*).
4. Une minute plus tard, tout le monde voit la nouvelle version.

Le paramètre `?admin` ne protège rien : il cache juste le bouton aux visiteurs.
Publier reste impossible sans accès au dépôt, donc personne d'autre ne peut modifier le site.

### À la main

Éditer `data.json` directement sur github.com (icône crayon). Structure :

```json
{
  "org": {
    "ceo": "Nexola",
    "coceo": "Hirosai",
    "tiktok": "https://www.tiktok.com/@...",
    "instagram": "https://www.instagram.com/...",
    "twitch": "",
    "discord": ""
  },
  "teams": {
    "tempest": {
      "logo": "",
      "players": [
        { "id": "a1", "role": "Tank", "pseudo": "Nexola", "heroes": "Reinhardt, Sigma" }
      ]
    }
  }
}
```

- `role` : Tank, DPS, Support, Flex, Remplaçant, Coach ou Manager.
- `heroes` : les héros séparés par des virgules.
- `id` : n'importe quelle chaîne, du moment qu'elle est unique dans l'équipe.
- `logo` : laisser vide, ou une image encodée en `data:image/png;base64,...`
  (c'est ce que produit l'éditeur intégré).

## Nom de domaine

GitHub Pages accepte un domaine personnalisé : acheter le domaine, puis
*Settings → Pages → Custom domain*. Le HTTPS est fourni gratuitement.
