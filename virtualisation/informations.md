
# Virtualisation & Infrastructures Hyperconvergées – Fiche Synthèse

Cette fiche synthétise les **concepts clés de la virtualisation** et les différences entre plusieurs solutions courantes : **Proxmox**, **ESXi**, **oVirt**, **Nutanix**, ainsi que des notions liées à l'**hyperconvergence** et aux **CDN**.

---

## Concepts de base

- **Hyperviseur de type 1** : tourne directement sur le matériel (ex. ESXi, Proxmox, oVirt)
- **Hyperviseur de type 2** : tourne au-dessus d’un OS hôte (ex. VirtualBox, VMware Workstation)
- **vCPU** : cœur virtuel assigné à une VM
- **Overcommit** : sur-allocation des ressources physiques

---

## Solutions de virtualisation

### Proxmox VE

- Basé sur Debian + KVM (hyperviseur) + LXC
- Interface web complète, accès en ligne de commande
- Supporte les clusters, live migration, ZFS natif
- Open source
- Gestion intégrée des backups/snapshots
- Idéal en lab comme en prod (flexible, peu gourmand)

### VMware ESXi

- Hyperviseur de type 1 propriétaire
- Interface web + vSphere pour la gestion avancée
- Performant, mature, très utilisé en entreprise
- Gestion fine des ressources, HA/DRS avec vCenter
- Fonctionnalités avancées payantes (licences)

### oVirt

- Projet open source soutenu par Red Hat (basé sur KVM)
- Interface de gestion web complète (via oVirt Engine)
- Moins user-friendly que Proxmox mais très modulaire
- Intégration avec Ansible, Foreman, RHV
- Utilisé dans des datacenters souhaitant rester open source

### Nutanix (AHV)

- Plateforme hyperconvergée tout-en-un (stockage, compute, réseau)
- AHV = hyperviseur intégré basé sur KVM
- Très orienté entreprise (simplicité, résilience, support)
- Administration via Prism (interface centralisée)
- Fonctionnalités avancées : snapshots, réplication, scale-out
- Très cher, mais fiable et bien intégré

---

## Hyperconvergence (HCI)

- Intègre **stockage, calcul, réseau** dans un seul bloc logiciel
- Déploiement simplifié, évolutif (scale-out)
- Idéal pour datacenters modernes
- Solutions HCI : Nutanix, VMware vSAN, Proxmox + Ceph

---

## CDN – Content Delivery Network

- Réseau distribué de serveurs répliquant du contenu (images, vidéos, JS…)
- But : rapprocher le contenu de l’utilisateur final
- Réduction de la latence, meilleure disponibilité
- Exemples : Cloudflare, Akamai, Fastly, AWS CloudFront

---

## Tableau comparatif

| Solution   | Type       | Licence       | Interface    | HCI Ready | Notes |
|------------|------------|----------------|--------------|-----------|-------|
| Proxmox    | KVM + LXC  | Open Source    | Web + CLI    | Oui (Ceph)| Léger et flexible |
| ESXi       | Type 1     | Propriétaire   | Web + vSphere| Oui (vSAN)| Très utilisé en prod |
| oVirt      | KVM        | Open Source    | Web          | Partiel   | Complexe à déployer |
| Nutanix    | AHV (KVM)  | Propriétaire   | Prism (Web)  | Oui       | Solution clé en main |
| VirtualBox | Type 2     | Libre          | GUI          | Non       | Pour usage local/dev |

---
