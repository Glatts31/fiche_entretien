# Gestion des paquets – Linux & FreeBSD

Cette fiche regroupe les principales commandes liées à la **gestion des paquets** sur différentes distributions Linux (Debian, Red Hat, SUSE, Arch Linux).

---

## Debian / Ubuntu – `apt`

```bash
sudo apt update                     # Met à jour la liste des paquets
sudo apt upgrade                    # Met à jour les paquets installés
sudo apt install nom_du_paquet      # Installe un paquet
sudo apt remove nom_du_paquet       # Supprime un paquet
sudo apt purge nom_du_paquet        # Supprime un paquet + config
sudo apt autoremove                 # Supprime les dépendances inutilisées
apt search nom                      # Recherche un paquet
apt show nom_du_paquet              # Infos détaillées sur un paquet
```

---

## Red Hat / CentOS / Fedora / Rocky – `dnf` (ou `yum`)

```bash
sudo dnf check-update               # Vérifie les mises à jour
sudo dnf upgrade                    # Met à jour les paquets
sudo dnf install nom_du_paquet      # Installe un paquet
sudo dnf remove nom_du_paquet       # Supprime un paquet
sudo dnf autoremove                 # Supprime les dépendances inutiles
dnf search nom                      # Recherche un paquet
dnf info nom_du_paquet              # Infos détaillées
```

> Pour RHEL/CentOS 7 : c'est `yum`.

---

## openSUSE / SUSE Linux – `zypper`

```bash
sudo zypper refresh                 # Rafraîchit les dépôts
sudo zypper update                  # Met à jour les paquets
sudo zypper install nom_du_paquet   # Installe un paquet
sudo zypper remove nom_du_paquet    # Supprime un paquet
zypper search nom                   # Recherche un paquet
zypper info nom_du_paquet           # Détails sur un paquet
```

---

## Arch Linux / Manjaro – `pacman`

```bash
sudo pacman -Syu                    # Mise à jour globale du système
sudo pacman -S nom_du_paquet        # Installe un paquet
sudo pacman -R nom_du_paquet        # Supprime un paquet
sudo pacman -Rns nom                # Supprime avec dépendances & configs
pacman -Ss nom                      # Recherche dans les dépôts
pacman -Qi nom_du_paquet            # Détails d’un paquet installé
```

---
