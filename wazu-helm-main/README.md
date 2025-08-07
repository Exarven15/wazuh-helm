# Wazuh Helm Chart

Ce dépôt contient un Helm chart permettant de déployer **Wazuh 4.12.0** dans un cluster Kubernetes (K3s, RKE2, ou autre), avec des ressources CPU limitées et une configuration de stockage compatible avec **Rook Ceph** (`rook-ceph-block`).

---

## 📦 Contenu

- `wazuh-manager`: StatefulSet du manager principal
- `wazuh-worker`: StatefulSet du worker (facultatif pour haute dispo)
- `wazuh-indexer`: StatefulSet de l'indexer
- `wazuh-dashboard`: Déploiement de l'interface graphique

---

## ⚙️ Pré-requis

- Un cluster Kubernetes fonctionnel (K3s, RKE2, etc.)
- Helm installé (`helm version`)
- `kubectl` configuré pour accéder au cluster
- Une `StorageClass` nommée `rook-ceph-block` disponible

---

## 🚀 Installation

### 1. Cloner le dépôt

```bash
git clone https://github.com/<ton-utilisateur>/wazuh-helm.git
cd wazuh-helm

kubectl get nodes

helm install wazuh . -n wazuh --create-namespace
```
### 2. Vérification
```bash
kubectl get pods -n wazuh
```

### 3. Accès au dashboard
```bash
kubectl get svc -n wazuh
```
Repère la ligne du service wazuh-dashboard (type ClusterIP ou NodePort) et accède à l’interface depuis un navigateur :
```bash
https://<IP>:<PORT>
```

Identifiants par défaut

    Nom d’utilisateur : admin
    Mot de passe : SecretPassword

