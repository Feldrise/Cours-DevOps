# Travaux Pratiques : Mise en Place d'un Ingress sur Kubernetes

## Partie 3 : Configuration et Utilisation d'Ingress dans Kubernetes
**Durée estimée : 1h30**

### Objectifs
- Comprendre le rôle et l'importance d'un Ingress dans un environnement Kubernetes.
- Pratiquer la configuration d'un Ingress pour gérer l'accès externe aux services.

### Étapes et Détails des Fichiers YAML

1. **Introduction à Ingress :**
   - Ingress est un objet API qui gère l'accès externe aux services dans un cluster, typiquement HTTP.
   - Ingress peut fournir l'équilibrage de charge, la terminaison SSL et l'hébergement virtuel basé sur le nom.

2. **Prérequis :**
   - Assurez-vous qu'un contrôleur Ingress est installé dans votre cluster. Par exemple, NGINX Ingress Controller ou Traefik.

3. **Création du Fichier YAML pour Ingress :**
   - Ouvrez votre éditeur de texte et créez un fichier nommé `ingress.yaml`.
   - Voici un exemple de fichier YAML pour configurer un Ingress :
     ```yaml
     apiVersion: networking.k8s.io/v1
     kind: Ingress
     metadata:
       name: example-ingress
       annotations:
         nginx.ingress.kubernetes.io/rewrite-target: /
     spec:
       rules:
       - host: monapp.exemple.com
         http:
           paths:
           - path: /
             pathType: Prefix
             backend:
               service:
                 name: nginx-service
                 port:
                   number: 80
     ```
   - **Explications :**
     - **metadata:** Définit le nom et les annotations spécifiques au contrôleur Ingress.
     - **spec:** Définit les règles d'accès. Ici, le trafic pour `monapp.exemple.com` est dirigé vers le service `nginx-service`.

4. **Application du Fichier YAML :**
   - Utilisez `kubectl apply -f ingress.yaml` pour créer l'Ingress.
   - Vérifiez le statut avec `kubectl get ingress`.

### Exercices de Prise d'Initiative
- **Configuration de Plusieurs Chemins :** Essayez d'ajouter plusieurs chemins dans votre fichier Ingress pour diriger le trafic vers différents services.
- **Sécurisation de l'Ingress :** Ajoutez une configuration pour la prise en charge de HTTPS en utilisant des certificats TLS et l'utilisation de certbot.

### Conseils et Bonnes Pratiques
- **Validation du Fichier YAML :** Assurez-vous que votre fichier Ingress est correctement formaté et valide. Utilisez des outils de validation YAML si nécessaire.
- **Tests :** Après avoir appliqué votre configuration Ingress, testez l'accès à vos services à partir d'un navigateur ou d'un outil de requête HTTP pour vous assurer que la configuration fonctionne comme prévu.
- **Sécurité :** Pensez à sécuriser votre Ingress, surtout si vous exposez des services sur Internet. La mise en place de HTTPS est une étape importante pour protéger le trafic.

---

Cet exercice vous permet de comprendre comment les objets Ingress fonctionnent dans Kubernetes et comment ils peuvent être utilisés

pour gérer efficacement l'accès externe à vos services. Avec Ingress, vous avez une plus grande flexibilité pour router le trafic et appliquer des règles plus complexes, ce qui est essentiel pour les applications modernes basées sur le web. N'oubliez pas que la pratique est essentielle pour maîtriser ces concepts. Alors, expérimentez autant que possible et observez comment les modifications affectent l'accès à vos services. Bonne découverte ! 🌐💡🚀