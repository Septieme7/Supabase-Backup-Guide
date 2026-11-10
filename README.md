# Guide de Sauvegarde Supabase

[![Repo GitHub](https://img.shields.io/badge/GitHub-Supabase--Backup--Guide-0070d1?style=plastic&logo=github&logoColor=white)](https://github.com/Septieme7/Supabase-Backup-Guide)
[![GitHub Pages](https://img.shields.io/badge/Live-GitHub%20Pages-00d4ff?style=plastic&logo=githubpages&logoColor=white)](https://septieme7.github.io/Supabase-Backup-Guide/)
[![License](https://img.shields.io/badge/License-MIT-8b5cf6?style=plastic)](https://opensource.org/licenses/MIT)

## Pourquoi ce guide existe

Quand j'ai commencé à utiliser Supabase sur un projet réel, je me suis rendu compte qu'il n'existe aucun bouton "Sauvegarder ma base" dans le dashboard. La sauvegarde passe obligatoirement par une CLI, un environnement Docker fonctionnel, une connexion PostgreSQL correctement configurée, et une compréhension précise des rôles et des permissions.

J'ai perdu plusieurs heures à déchiffrer des erreurs peu explicites : "Connection refused" parce que Docker Desktop n'était pas lancé, "network unreachable" parce que ma box ne gérait pas l'IPv6, "permission denied" parce que je n'étais pas Owner de l'organisation. J'ai aussi failli oublier les fichiers du Storage, qui ne sont pas inclus dans le dump SQL, ainsi que les secrets chiffrés du module Vault.

Plutôt que de garder ces notes dans un fichier local que j'aurais fini par perdre, je les ai transformées en guide structuré, en espérant que ça évite à d'autres les mêmes tâtonnements.

## Ce que ce guide apporte

- Une méthode reproductible pour extraire l'intégralité de la base de données en trois fichiers SQL distincts (schéma, données, rôles), directement réutilisables pour une restauration.
- Une explication claire de la différence entre la connexion Direct (IPv6) et le Session Pooler (IPv4), pour comprendre pourquoi certaines connexions échouent selon les réseaux et comment choisir la bonne.
- La démarche pour sauvegarder les fichiers physiques hébergés dans le Storage, qui ne figurent jamais dans un dump PostgreSQL classique.
- Un rappel sur le module Vault et sur la Root Key, dont l'absence rend toute restauration de données chiffrées impossible.
- Des commandes prêtes à copier, des captures d'écran du dashboard Supabase et des avertissements sur les points bloquants.

## À qui s'adresse ce guide

Aux développeurs qui utilisent Supabase en production et qui cherchent une sauvegarde manuelle fiable et documentée. Aux équipes qui préparent une migration, un changement de plan tarifaire, ou un plan de reprise après sinistre. Et à toute personne qui s'est déjà demandé, un soir de déploiement, ce qui se passerait si la base disparaissait du jour au lendemain.

## Voir le guide en ligne

Le guide complet est consultable directement à l'adresse suivante :

https://septieme7.github.io/Supabase-Backup-Guide/

## Contribution

Les retours et suggestions sont bienvenus. Si tu repères une erreur, un cas non couvert, ou une méthode plus fiable sur une version récente de Supabase, ouvre une issue ou propose une pull request.

---

Fait avec 💖 et passion By [LvSs7](https://github.com/Septieme7)