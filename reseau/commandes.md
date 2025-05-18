# Réseau – Configuration & Diagnostic

Cette fiche regroupe les commandes de base pour configurer, diagnostiquer et surveiller le réseau sur **Linux** et **FreeBSD**.

---

## Affichage des interfaces

### Linux

```bash
ip a               # Affiche les interfaces et adresses IP
ip r               # Affiche la table de routage
```

### FreeBSD

```bash
ifconfig           # Équivalent de `ip a` sur BSD
netstat -rn        # Table de routage
```

---

## Configuration manuelle (temporaire)

### Linux (avec `ip`)

```bash
ip a add 192.168.1.10/24 dev eth0
ip r add default via 192.168.1.1
```

### FreeBSD (avec `ifconfig`)

```bash
ifconfig em0 inet 192.168.1.10 netmask 255.255.255.0
route add default 192.168.1.1
```

---

## Configuration persistante

### Linux (Debian)

```ini
/etc/network/interfaces
```

### Linux (systemd-networkd)

```ini
/etc/systemd/network/10-static.network
```

### FreeBSD

Fichier : `/etc/rc.conf`

```conf
ifconfig_em0="inet 192.168.1.10 netmask 255.255.255.0"
defaultrouter="192.168.1.1"
```

---

## Outils de diagnostic

```bash
ping 8.8.8.8                 # Test ICMP
ping -c 4 google.com         # Test DNS + ICMP
traceroute google.com       # Trace du chemin
dig google.com              # Résolution DNS
host google.com             # Résolution alternative
nslookup google.com         # Obsolète mais encore courant
```

---

## Utilitaires utiles

```bash
netstat -laputen             # Ports ouverts (Linux)
ss -laputen                  # Ports ouverts (plus moderne, Linux)
sockstat -l                  # Ports ouverts (FreeBSD)
tcpdump -i em0               # Capture réseau (root)
```

---

## Fichiers importants

| Système | Fichier                         | Rôle                         |
|---------|----------------------------------|------------------------------|
| Linux   | /etc/resolv.conf                | Serveurs DNS                 |
| Linux   | /etc/network/interfaces         | Config réseau (Debian)       |
| FreeBSD | /etc/rc.conf                    | Config IP & routes           |
| FreeBSD | /etc/resolv.conf                | Serveurs DNS                 |

---
