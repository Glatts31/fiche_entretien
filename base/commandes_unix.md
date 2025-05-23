# Commandes de base communes Linux / FreeBSD

Ce mémo regroupe les **commandes Unix de base** valides à la fois sur **Linux** et **FreeBSD**.

---

## Navigation & système de fichiers

```bash
pwd                          # Affiche le chemin courant
ls -la                       # Liste les fichiers avec détails / fichiers cachés
cd /tmp                      # Change de répertoire
mkdir dossier                # Crée un dossier
touch fichier.txt            # Crée un fichier vide
cp source dest               # Copie un fichier
mv source dest               # Déplace ou renomme un fichier
rm fichier.txt               # Supprime un fichier
rm -rf dossier               # Supprime un dossier récursivement
rmdir dossier                # Supprime un dossier s'il est vide
```

---

## Fichiers & contenu

```bash
cat fichier.txt              # Affiche le contenu
less fichier.txt             # Affichage page par page
head -n 10 fichier           # Affiche les 10 premières lignes
tail -f fichier.log          # Suivi en temps réel (log) ce qui s'écrit à la fin du contenu d'un fichier
wc -l fichier.txt            # Compte les lignes
sort fichier.txt             # Trie les lignes
grep "mot" fichier           # Recherche une chaîne
find /etc -name "*.conf"     # Recherche de fichiers
```

---

## Informations système

```bash
uname -a                     # Infos système et noyau
uptime                       # Durée de fonctionnement
df -h                        # Utilisation des systèmes de fichiers
du -sh /var/log              # Taille du dossier
top                          # Processus en temps réel
ps aux | grep <processus>    # Recherche de processus
kill <PID>                   # Termine un processus
pkill nom                    # Tuer un processus par nom
pgrep nom                    # Affiche les PID d'un processus
```

---

## Utilisateurs, Droits et permissions

```bash
whoami                       # Affiche l'utilisateur courant
id                           # UID, GID et groupes
groups                       # Liste des groupes de l'utilisateur
adduser nom                  # Ajoute un utilisateur (BSD)
useradd nom                  # Ajoute un utilisateur (Linux)
passwd nom                   # Définit ou change le mot de passe
usermod -aG groupe nom       # Ajoute un utilisateur à un groupe (Linux)
pw usermod nom -G groupe     # Ajoute un utilisateur à un groupe (FreeBSD)
deluser nom                  # Supprime un utilisateur (Linux)
rmuser nom                   # Supprime un utilisateur (FreeBSD)
chmod 755 script.sh          # Modifie les permissions
chown user:group fichier     # Change propriétaire/groupe
```


⚠️ **Attention :** Particularités BSD
- Utilisation de `pw` pour la gestion des utilisateurs (ex : `pw useradd`, `pw groupadd`)
- Fichier `/etc/rc.conf` pour gérer les services lancés au boot (vs systemd sur Linux)
- Le fichier sudoers se trouve aussi dans `/usr/local/etc/sudoers` 

---

## Sudo & Élévation de privilèges

```bash
sudo commande              # Exécute une commande en root
sudo su -                  # Passe en superutilisateur (`sudo -i `)
visudo                     # Édite le fichier sudoers (via EDITOR)
```

---

## Réseau (de base)

```bash
ping 8.8.8.8                 # Test de connectivité
ifconfig                     # Affiche les interfaces (FreeBSD)
ip a                         # Affiche les interfaces (Linux)
netstat -rn                  # Table de routage
sockstat -l                  # Ports à l'écoute (FreeBSD)
ss -tuln                     # Ports à l'écoute (Linux)
```

---
