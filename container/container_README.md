
# Conteneurisation – Docker & Jails

Ce dossier regroupe toutes les ressources liées à la **conteneurisation**, qu’elle soit utilisée dans un contexte **Linux** avec **Docker**, ou **FreeBSD** avec **Jails**.

---

## [Docker](docker.md) (Linux)

Docker est le moteur de conteneurisation le plus populaire sur Linux. Il permet de créer, lancer et orchestrer des conteneurs de manière simple et reproductible.  
Dans ce dossier, tu trouveras :

- Les commandes de base (`run`, `exec`, `build`, etc.)
- L’usage de volumes et réseaux
- L’utilisation de `docker-compose`
- La mise en place d’un registry Docker privé
- La gestion des tags et des registries
- Les bonnes pratiques de nettoyage

---

## [Jail](jail.md) (FreeBSD)

Les **jails** sont une technologie de conteneurisation native de FreeBSD. Elles offrent une isolation forte au niveau du système d’exploitation, sans recourir à la virtualisation.

Ce dossier contient :

- La gestion des jails avec les outils natifs (`jail.conf`, `jail`, etc.)
- Des exemples de configuration réseau, création, destruction

---
