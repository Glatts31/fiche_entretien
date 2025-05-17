# Conteneurisation avec Jails – FreeBSD

Les **jails** sont le mécanisme natif de conteneurisation sur FreeBSD, offrant un environnement isolé au niveau système.

---

## ⚙️ Concepts de base

- Une jail est un sous-système isolé avec son propre `/`, utilisateurs, services, etc.
- Elle partage le noyau FreeBSD avec l’hôte.
- Isolation : utilisateurs, réseau, système de fichiers, processus.

---

## Création d’une jail avec les outils natifs

### Préparer l’environnement

```bash
sysrc jail_enable=YES
service jail start
```

### Déclaration dans `/etc/jail.conf`

```conf
webjail {
    host.hostname = web.local;
    path = /usr/jails/webjail;
    ip4.addr = 192.168.1.10;
    interface = em0;
    persist;
}
```

### Création du système de fichiers

```bash
mkdir -p /usr/jails/webjail
cd /usr/jails/webjail
tar -xvf /usr/freebsd-dist/base.txz -C .
```

### Lancer la jail

```bash
jail -c webjail
```

### Commandes utiles

```bash
jls          # Permet de voir les jails avec les JID associés
jexec JID    # Similaire à docker run -it pour Docker
jail -r JID  # Supprime l'exécution de la Jail
```

---

## 🔐 Réseau et sécurité

- Jails peuvent avoir des IP statiques, NAT, loopback
- `vnet` permet d'isoler le réseau via bridge
- Sécurité renforcée via `security.jail.*` dans `sysctl`

---
