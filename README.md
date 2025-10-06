ansible-role-k8s-install-3k
=========

Ce rôle Ansible installe et configure les composants nécessaires à un cluster Kubernetes : kubelet, kubeadm, kubectl ainsi que le runtime containerd et les plugins CNI.
Il applique également les configurations système indispensables au bon fonctionnement de Kubernetes (swap désactivé, modules noyau, paramètres sysctl, etc.).

Requirements
------------

- **OS supporté** : Ubuntu 20.04+ / Debian 11+
- **Kernel** : version >= 4.0
- **Mémoire** : minimum 2 Go RAM par nœud
- Accès root ou utilisateur avec privilèges sudo
- Connexion internet (pour télécharger containerd, runc, CNI et les paquets Kubernetes)

Role Variables
--------------

Variables par défaut (définies dans defaults/main.yml) :

```yaml
k8s_version: "v1.34"
containerd_version: "2.1.4"
runc_version: "1.3.1"
cni_plugins_version: "1.8.0"
```
Mais on peut les surcharger selon nos besoins (par exemple, pour installer une version spécifique de Kubernetes ou de containerd).

Dependencies
------------

Aucune dépendance directe avec d’autres rôles Ansible, mais il est recommandé d’avoir :
- Un rôle de sécurisation de base (firewall, SSH, utilisateurs, etc.) avant de déployer Kubernetes.
- Un rôle de gestion réseau si tu veux installer un CNI spécifique comme Calico, Flannel ou Cilium.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: k8s_nodes
  become: yes
  roles:
    - role: ansible-role-k8s-install-3k
      vars:
        k8s_version: "v1.34"
```

License
-------

BSD

Author Information
------------------

Nom: AUGET  
Prénom: Rabina  
Adresse mail: rabinauget@gmail.com  
LinkdIn: https://www.linkedin.com/in/rabina-auget-61663314a
