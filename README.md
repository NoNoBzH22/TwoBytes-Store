# TwoBytes Store

Store d'applications tiers pour [ZimaOS](https://www.zimaspace.com/) et [CasaOS](https://casaos.io/).

| Application | Description | Langue | Port |
|---|---|---|---|
| [Agora](Apps/Agora) | Recherche multi-sources à plugins, métadonnées TMDB, envoi vers JDownloader | Français | 3067 |
| [DVinyl](Apps/DVinyl) | Gestion de collections physiques (vinyles, CD, livres, films, jeux, LEGO) par [Kyonew](https://github.com/Kyonew/DVinyl) | Multilingue (EN, FR, DE, ES, IT) | 3099 |

## Ajouter le store

Dans ZimaOS (1.7 et plus) : **App Store** > **Sources** > ajouter l'URL :

```
https://raw.githubusercontent.com/NoNoBzH22/TwoBytes-Store/gh-pages
```

Sur CasaOS et les anciennes versions de ZimaOS, qui n'acceptent que les archives :

```
https://github.com/NoNoBzH22/TwoBytes-Store/archive/refs/heads/main.zip
```

## Publication

À chaque push sur `main`, l'action [publish.yml](.github/workflows/publish.yml) construit le store au format v2 (`index.json`, `store.json`, `apps/<id>/`) avec [build-appstore-action](https://github.com/IceWhaleTech/build-appstore-action), puis le publie sur la branche `gh-pages`.

## Données

Chaque application range ses données dans `/DATA/AppData/<app>/`.

- **Agora** : `data/` (réglages, comptes, plugins, bases SQLite) et `downloads/` (fichiers `.crawljob` pour JDownloader).
- **DVinyl** : `mongo/` (la base), `uploads/` (images) et `secrets/` (`PASSJWT` et `SESSION_SECRET`, générés au premier démarrage).

## Ajouter une application

Un dossier par application dans `Apps/`, avec un `docker-compose.yml` portant les métadonnées `x-casaos` et ses images (`icon.png`, captures). Les URL des images pointent vers `https://raw.githubusercontent.com/NoNoBzH22/TwoBytes-Store/main/Apps/<App>/icon.png` ; le build les recopie dans `gh-pages`.
