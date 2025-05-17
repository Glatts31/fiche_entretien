
# Commandes K8S de base

## Gestion du cluster

| Objectif                            | Commande |
|-------------------------------------|----------|
| Afficher les infos du cluster       | `kubectl cluster-info` |
| Lister les nœuds                    | `kubectl get nodes` |
| Voir la version de Kubernetes       | `kubectl version --short` |

---

## Ressources Kubernetes

| Objectif                              | Commande |
|---------------------------------------|----------|
| Lister tous les objets (pods, svc…)   | `kubectl get all -A` |
| Lister les pods (namespace courant)   | `kubectl get pods` |
| Lister les pods (tous namespaces)     | `kubectl get pods -A` |
| Lister les pods dans un namespace     | `kubectl get pods -n <namespace>` |
| Lister les namespaces                 | `kubectl get ns` |
| Lister les services                   | `kubectl get svc -A` |
| Lister les déploiements               | `kubectl get deployments -A` |
| Lister les Ingress (URL)              | `kubectl get ingress -A` |

---

## Exploitation & Debug

| Objectif                                  | Commande |
|-------------------------------------------|----------|
| Décrire un objet (pod, node, svc…)        | `kubectl describe pod <nom> -n <namespace>` |
| Accéder à un pod                          | `kubectl exec -it <pod> -- bash` ou `sh` |
| Voir les logs d’un pod                    | `kubectl logs <pod>` |
| Voir les logs d’un container spécifique   | `kubectl logs <pod> -c <container>` |
| Redémarrer un déploiement                  | `kubectl rollout restart deployment <nom>` |
| Voir le statut du déploiement              | `kubectl rollout status deployment <nom>` |

---

## Manipulation des ressources

| Objectif                             | Commande |
|--------------------------------------|----------|
| Créer un objet                       | `kubectl create -f fichier.yaml` |
| Appliquer des modifications          | `kubectl apply -f fichier.yaml` |
| Supprimer un objet                   | `kubectl delete -f fichier.yaml` |
| Supprimer un pod                     | `kubectl delete pod <nom>` |
| Supprimer un déploiement             | `kubectl delete deploy <nom>` |

⚠️ **Attention :** Si on agit sur un namespace bien utiliser `-n <namespace>` dans la commande.

Pour définir le namespace par défaut : `kubectl config set-context --current --namespace=<namespace>`

---

## URL d’accès & exposition

| Objectif                                | Commande |
|-----------------------------------------|----------|
| Lister les ingress                      | `kubectl get ingress -A` |
| Détails d’un ingress                    | `kubectl describe ingress <nom> -n <namespace>` |

---