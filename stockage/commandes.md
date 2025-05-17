# Stockage – Gestion des disques et systèmes de fichiers (Linux & FreeBSD)

Cette fiche couvre les opérations essentielles liées à la gestion des **disques, partitions, systèmes de fichiers et montage**, valables sur **Linux** et **FreeBSD**.

---

## Monter / démonter un système de fichiers

```bash
mount                     # Affiche les systèmes montés
df -h                     # Affiche l’utilisation disque (lisible)
umount /mnt/volume        # Démonte un volume
```

### Montage manuel

```bash
mount /dev/sdX1 /mnt              # Linux
mount /dev/ada0p1 /mnt            # FreeBSD
```

---

## Modifier le fichier `/etc/fstab`

Ce fichier permet de monter automatiquement les systèmes de fichiers au démarrage.

```fstab
/dev/sda1   /mnt/data   ext4    defaults    0 2
/dev/ada0p2 /mnt/zdata  zfs     rw          0 0
```

> Utiliser `mount -a` pour tester la validité du fichier `fstab`.

---

## Partitionnement

### Linux (avec `fdisk`, `lsblk`, `parted`)

```bash
lsblk                          # Affiche les périphériques blocs
sudo fdisk /dev/sdX            # Outil de partitionnement interactif
sudo parted /dev/sdX           # Alternative avec GPT support
```

### FreeBSD (avec `gpart`)

```bash
gpart show                     # Affiche la table de partition
gpart create -s GPT ada0       # Crée un schéma GPT
gpart add -t freebsd-zfs -s 10G ada0  # Ajoute une partition ZFS
```

---

## Création et formatage de systèmes de fichiers

### Linux

```bash
mkfs.ext4 /dev/sdX1            # Formate en ext4
mkfs.xfs /dev/sdX2             # Formate en XFS
```

### FreeBSD

```bash
newfs /dev/ada0p1              # Formate en UFS
```

---

## ZFS – Système de fichiers avancé

### Création d’un pool ZFS

```bash
zpool create tank /dev/ada1
zfs create tank/dataset
zfs list
```

### Démontage & destruction

```bash
zfs umount tank/dataset
zfs destroy tank/dataset
zpool destroy tank
```

> ZFS est **nativement supporté sur FreeBSD**, mais nécessite une installation spécifique sur Linux.

---

## LVM (Linux Volume Manager)

### Initialisation et création de volumes

```bash
pvcreate /dev/sdX1                   # Initialise le disque comme volume physique
vgcreate mon_vg /dev/sdX1           # Crée un groupe de volumes
lvcreate -L 10G -n mon_lv mon_vg    # Crée un volume logique de 10 Go
mkfs.ext4 /dev/mon_vg/mon_lv        # Formate le volume logique
mount /dev/mon_vg/mon_lv /mnt       # Monte le volume
```

### Extension d’un volume logique et du système de fichiers

```bash
lvextend -L +5G /dev/mon_vg/mon_lv        # Étend le volume logique
resize2fs /dev/mon_vg/mon_lv              # Étend le FS (ext4)
xfs_growfs /mnt                           # /mnt = point de montage actif (xfs)
```

---

## Vérification & santé

```bash
fsck /dev/sdX1           # Vérifie un système de fichiers (Linux)
zpool status             # État du pool ZFS
zpool scrub tank         # Vérification d’intégrité ZFS
```

---
