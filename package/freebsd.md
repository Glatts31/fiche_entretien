# 📦 Gestion des paquets sur FreeBSD

FreeBSD dispose de deux méthodes principales pour installer des logiciels :

- Le **système de paquets binaires** (`pkg`)
- Le **système des ports** (`/usr/ports/`) pour compiler les logiciels depuis les sources

---

## Utilisation de `pkg` (paquets binaires)

```bash
sudo pkg update                  # Met à jour l'index des paquets
sudo pkg upgrade                 # Met à jour tous les paquets installés
sudo pkg install nom_paquet      # Installe un paquet
sudo pkg delete nom_paquet       # Supprime un paquet
pkg search mot_cle               # Recherche un paquet
pkg info nom_paquet              # Affiche les détails d’un paquet
pkg info                         # Liste tous les paquets installés
```

> Les paquets sont installés dans `/usr/local`.

---

## Utilisation des ports (compilation)

```bash
cd /usr/ports/sysutils/htop
sudo make install clean
```

- Permet de **compiler depuis les sources** en personnalisant les options
- Nécessite les **sources des ports**, installables via :
  ```bash
  portsnap fetch extract         # Téléchargement initial
  portsnap fetch update          # Mise à jour
  ```

---

## Emplacement des logiciels

| Type | Répertoire |
|------|------------|
| Binaire système | `/bin`, `/sbin`, `/usr/bin`, `/usr/sbin` |
| Logiciels installés par pkg/ports | `/usr/local/bin`, `/usr/local/sbin` |

---

## Vérification d'intégrité

```bash
pkg check -Ba                    # Vérifie la base des paquets installés
```

---

## Nettoyage

```bash
pkg autoremove                   # Supprime les dépendances inutilisées
pkg clean                        # Nettoie le cache local des paquets
```

---
