# TwoBytes Store

Store d'applications tiers pour [ZimaOS](https://www.zimaspace.com/) et [CasaOS](https://casaos.io/).

| Application | Description | Port |
|---|---|---|
| [Agora](Apps/Agora) | Recherche multi-sources à plugins, métadonnées TMDB, envoi vers JDownloader | 3067 |
| [DVinyl](Apps/DVinyl) | Gestion de collections physiques (vinyles, CD, livres, films, jeux, LEGO) par [Kyonew](https://github.com/Kyonew/DVinyl) | 3099 |

## Ajouter le store

Dans ZimaOS : **App Store** > **Sources** (ou « More apps ») > ajouter l'URL :

```
https://github.com/NoNoBzH22/TwoBytes-Store/archive/refs/heads/main.zip
```

Sur CasaOS, en ligne de commande :

```bash
casaos-cli app-management register app-store https://github.com/NoNoBzH22/TwoBytes-Store/archive/refs/heads/main.zip
```

## Données

Chaque application range ses données dans `/DATA/AppData/<app>/`.

- **Agora** : `data/` (réglages, comptes, plugins, bases SQLite) et `downloads/` (fichiers `.crawljob` pour JDownloader).
- **DVinyl** : `mongo/` (la base), `uploads/` (images) et `secrets/` (`PASSJWT` et `SESSION_SECRET`, générés au premier démarrage).

## Ajouter une application

Un dossier par application dans `Apps/`, avec un `docker-compose.yml` portant les métadonnées `x-casaos` et ses images (`icon.png`, captures). Les URL des images passent par jsDelivr : `https://cdn.jsdelivr.net/gh/NoNoBzH22/TwoBytes-Store@main/Apps/<App>/icon.png`.
