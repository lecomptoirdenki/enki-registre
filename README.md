# Registre Enki — les sélections, déposées avant les matchs

Ce dépôt contient **une seule chose** : les sélections du modèle Enki, écrites
avant le coup d'envoi, et jamais retouchées ensuite.

La page se lit ici : **[le registre](https://registre.lecomptoirdenki.fr/)**

## Pourquoi ce dépôt existe

Un bilan de pronostics ne vaut rien si celui qui le publie peut le réécrire.
N'importe qui peut afficher un historique gagnant : il suffit d'oublier les jours
perdants.

La seule parade est l'horodatage par un tiers. Chaque journée est déposée ici
avant ses matchs, et **c'est la date du commit GitHub qui fait foi** — pas une
date écrite dans un fichier, qu'on pourrait taper soi-même. Réécrire l'histoire
d'un dépôt public laisse une trace visible.

## Comment vérifier

```bash
git log --diff-filter=A --format='%cI  %s' -- registre/2026-08-18.json
```

Cette commande donne la date à laquelle la journée a été déposée. Comparez-la aux
heures de coup d'envoi qui figurent dans le fichier : chaque sélection porte en
outre son propre horodatage de dépôt (`deposeLe`).

Pour voir tout ce qui a été touché depuis le premier jour :

```bash
git log --stat -- registre/
```

## Ce qu'un fichier contient

```json
{
 "jour": "2026-08-18",
 "publieLe": "2026-08-18T04:30:52.149Z",
 "selections": [
  {
   "id": "2026-08-18|Nautico PE|Ceará|dom",
   "heure": "02:30",
   "match": "Nautico PE – Ceará",
   "marche": "1N2",
   "camp": "1",
   "cote": 2.28,
   "resultat": { "score": "0-1", "gagne": false },
   "avant": true,
   "deposeLe": "2026-08-18T04:30:52.149Z"
  }
 ]
}
```

`avant: true` signifie que le coup d'envoi était encore devant au moment du dépôt.
`resultat` est ajouté après le match — c'est la **seule** modification autorisée.

## Les règles que ce dépôt s'impose

- Une journée déposée **ne se réécrit pas**.
- On peut **ajouter** une sélection tant que son match n'a pas commencé, et
  **seulement** dans ce cas.
- On peut **retirer** une sélection si le match disparaît du programme (report,
  annulation). Jamais parce que la cote a bougé, jamais parce qu'on ne referait
  plus ce choix : ce serait effacer un conseil réellement donné.
- Une fois le coup d'envoi passé, plus rien ne bouge que le résultat.
- Les jours perdants figurent comme les autres.

## Ce que ce dépôt ne contient pas

Aucune information sur la **règle** qui a produit une sélection : ni son niveau,
ni sa réussite, ni son effectif, ni un numéro qui permettrait de la suivre. Une
ligne dit ce qui a été conseillé, pas pourquoi.

## Avant l'ouverture du registre

Les journées antérieures au 18/08/2026 figurent dans `registre/_amorcage.json`.
Elles ont été **calculées** avant les matchs, avec le modèle dans l'état où il
était le matin même, mais **déposées après**. Elles sont donc présentées à part
sur la page, et n'entrent pas dans le décompte « déposées avant les matchs ».
