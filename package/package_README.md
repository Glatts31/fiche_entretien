# Gestion des paquets

Cette section du mémo est dédiée à la **gestion des paquets logiciels** sur les différents systèmes Unix-like.

---

## 🔹 Organisation

Le dossier est divisé en deux sous-parties principales :

- **[Linux](linux.md)** → commandes et outils pour les principales distributions Linux :
  - `apt` pour Debian, Ubuntu
  - `dnf/yum` pour RedHat, Fedora, CentOS, Rocky
  - `zypper` pour openSUSE
  - `pacman` pour Arch Linux

- **[FreeBSD](freebsd.md)** → commandes spécifiques à FreeBSD :
  - `pkg` : gestionnaire de paquets binaire
  - `/usr/ports` : compilation depuis les sources

---

## Objectif

- Installer, mettre à jour et supprimer des logiciels
- Comprendre les différences d’outils selon les systèmes
- Savoir quand utiliser `pkg`, `ports`, ou les outils comme `apt`, `dnf`, `zypper`, etc.

---

Chaque sous-répertoire contient un fichier Markdown explicatif et les commandes les plus utilisées pour le système concerné.
