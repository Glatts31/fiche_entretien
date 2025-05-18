# Services – Gestion des démons système (Linux & FreeBSD)

Cette fiche présente la gestion des services (démons) système, à travers les deux principaux environnements Unix : **Linux (systemd)** et **FreeBSD (rc.d)**.

---

## Linux – systemd

### Commandes principales

```bash
systemctl status nginx              # Voir le statut du service
systemctl start nginx               # Démarrer le service
systemctl stop nginx                # Arrêter le service
systemctl restart nginx             # Redémarrer
systemctl reload nginx              # Recharger la config
systemctl enable nginx              # Activer au démarrage
systemctl disable nginx             # Désactiver au démarrage
systemctl is-enabled nginx          # Vérifie si activé
```

### Logs du service

```bash
journalctl -u nginx.service         # Voir les logs
journalctl -xe                      # Logs système détaillés
```

---

## FreeBSD – rc.d

### Commandes principales

```bash
service nginx status                # Voir le statut du service
service nginx start                 # Démarrer
service nginx stop                  # Arrêter
service nginx restart               # Redémarrer
service nginx reload                # Recharger la configuration
```

### Activer au démarrage

Dans `/etc/rc.conf` :

```conf
nginx_enable="YES"
```

> Tous les services doivent être explicitement déclarés pour démarrer automatiquement.

### Voir les services actifs

```bash
service -e                         # Services actuellement activés
```

---

## Emplacements des fichiers

| Système  | Fichiers/Commandes                       | Rôle                       |
|----------|------------------------------------------|----------------------------|
| Linux    | `/etc/systemd/system/`                   | Services personnalisés     |
| Linux    | `systemctl`, `journalctl`                | Gestion des services       |
| FreeBSD  | `/etc/rc.conf`, `/usr/local/etc/rc.d/`   | Configuration des services |
| FreeBSD  | `service`, `rc.d`                        | Contrôle des services      |

---

## Créer un service systemd personnalisé

1. Crée un fichier de service :
```bash
vim /etc/systemd/system/mon-service.service
```

2. Exemple de contenu :
```ini
[Unit]
Description=Mon script perso
After=network.target

[Service]
ExecStart=/usr/local/bin/mon_script.sh
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

3. Recharger systemd et activer :
```bash
sudo systemctl daemon-reexec    # Ou daemon-reload
sudo systemctl enable mon-service
sudo systemctl start mon-service
```

4. Vérification :
```bash
systemctl status mon-service
```

---

## Créer un service rc.d personnalisé (FreeBSD)

1. Crée un script dans `/usr/local/etc/rc.d/` :
```bash
vi /usr/local/etc/rc.d/mon_script
```

2. Exemple de contenu :
```sh
#!/bin/sh

# PROVIDE: mon_script
# REQUIRE: DAEMON
# KEYWORD: shutdown

. /etc/rc.subr

name="mon_script"
rcvar=mon_script_enable

command="/usr/local/bin/mon_script.sh"
pidfile="/var/run/${name}.pid"

load_rc_config $name
: ${mon_script_enable:="NO"}

run_rc_command "$1"
```

3. Rendre le script exécutable :
```bash
chmod +x /usr/local/etc/rc.d/mon_script
```

4. Activer le service au démarrage :
Ajoute dans `/etc/rc.conf` :
```conf
mon_script_enable="YES"
```

5. Utiliser le service :
```bash
service mon_script start
service mon_script status
```

> Le script doit tourner en tâche de fond si nécessaire (ex: boucle `while true` ou gestion via `daemon`).
