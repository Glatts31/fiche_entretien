
# Conteneurisation avec Docker

Cette fiche couvre l’utilisation de base de Docker, y compris la gestion des conteneurs, images, volumes, réseaux, et la mise en place d’un **registry privé local**.

---

## Commandes de base

```bash
docker version                     # Version client + serveur
docker info                        # Infos du démon
docker ps                          # Conteneurs actifs
docker ps -a                       # Tous les conteneurs
docker images                      # Liste des images locales
docker pull nginx                  # Télécharge une image
docker run -it <conteneur> bash         # Lance un conteneur interactif
docker exec -it <nom_container> bash # Accède à un conteneur en cours
docker stop/start/restart ID/NOM   # Gère les conteneurs
docker rm ID/NOM                   # Supprime un conteneur
docker rmi IMAGE                   # Supprime une image
```

---

## Volumes et montages

```bash
docker volume create nom_volume
docker run -v nom_volume:/data ...          # Utilisation par nom
docker run -v $(pwd)/local:/data ...        # Montage local
docker volume ls
docker volume inspect nom_volume
```

---

## Réseaux Docker

```bash
docker network ls
docker network create mon_reseau
docker run --network=mon_reseau ...
```

---

## Dockerfile (exemple simple)

```Dockerfile
FROM alpine
RUN apk add --no-cache curl
CMD ["curl", "https://example.com"]
```

---

## docker-compose (exemple de base)

```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  redis:
    image: redis:alpine
```

> Lancer avec `docker-compose up -d` et arrêter avec `docker-compose down`.

---

## Créer un registry Docker local

```bash
docker run -d -p 5000:5000 --restart=always --name registry registry:2
```

- Accessible en local sur `localhost:5000`
- Stocke les images dans `/var/lib/registry` dans le conteneur

### Pousser une image dans le registry local

```bash
docker tag monimage localhost:5000/monimage
docker push localhost:5000/monimage
```

### Récupérer une image depuis le registry local

```bash
docker pull localhost:5000/monimage
```

---

## Gérer les tags d'une image Docker

```bash
docker images                # Liste les images avec leur TAG
docker tag source target     # Renomme ou tague une image
```

---

## Connexion à une registry distante

### Se connecter à une registry (ex. Docker Hub, GitLab, Harbor…)

```bash
docker login                 # Par défaut sur Docker Hub
docker login myregistry.com # Connexion à une registry personnalisée
```

> Après login, les identifiants sont stockés dans `~/.docker/config.json`.

### Se déconnecter

```bash
docker logout                # Pour Docker Hub
docker logout myregistry.com
```

---

## Nettoyage

```bash
docker system prune             # Supprime tous les objets non utilisés
docker image prune              # Supprime les images non utilisées
docker volume prune             # Supprime les volumes inutilisés
```

---
