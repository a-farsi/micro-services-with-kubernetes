### Déploiement des micro-services avec Kubernetes

L'objectif de ce mini-projet est de **déployer une application FastAPI** sur un cluster **K3s** en respectant les bonnes pratiques Kubernetes. Cela inclut : la configuration de **3 réplicas** pour l’application, le **déploiement de PostgreSQL en StatefulSet** avec une persistance des données via un **PVC**, ainsi que la gestion des **secrets** et **configurations** avec **Secrets** et **ConfigMaps**. Enfin, l’application est exposée à l’extérieur grâce à un **Ingress**.

#### Analyse de l'architecture
Nous devons déployer deux micro-services sur Kubernetes :
1. Une application FastAPI
2. Une base de données PostgreSQL

#### Architecture

L'architecture du déploiement est la suivante :
* **FastAPI** : 3 réplicas, accessible via un sous-domaine personnalisé
* **PostgreSQL** : Base de données avec stockage persistant de 10Gi, déployée en StatefulSet
* **PVC** : Stockage persistant avec accès ReadWriteMany
* **Ingress** : Pour exposer l'application FastAPI à l'extérieur avec un sous-domaine
* **Secrets** : Pour stocker les informations sensibles (mot de passe PostgreSQL)
* **ConfigMap** : Pour stocker les configurations non-sensibles (nom d'utilisateur, nom de base
de données) 

Tous les services sont déployés dans le namespace _standard_.