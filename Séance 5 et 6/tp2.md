# Travaux Pratiques : Configuration et Exposition d'une Application sur Kubernetes

## Partie 2 : Mise en Place et Exploration des Services Kubernetes
**Durée estimée : 1h30**

### Objectifs
- Comprendre comment exposer une application dans Kubernetes via différents types de Services.
- Pratiquer la création et la configuration de Services de type `LoadBalancer` et `NodePort`.

### Étapes et Détails des Fichiers YAML

1. **Introduction aux Services Kubernetes :**
   - Un Service Kubernetes est une abstraction qui définit comment exposer une application, un ensemble de Pods, à un réseau externe ou interne.

2. **Service de Type LoadBalancer :**
   - Utilisé pour exposer le Service à l'Internet public.
   - Distribue automatiquement le trafic externe entre les Pods.

   **Création du Fichier YAML pour LoadBalancer :**
   - Ouvrez votre éditeur de texte et créez un fichier nommé `loadbalancer-service.yaml`.
   - Voici un exemple de fichier YAML pour un Service de type `LoadBalancer` :
     ```yaml
     apiVersion: v1
     kind: Service
     metadata:
       name: nginx-loadbalancer
     spec:
       type: LoadBalancer
       ports:
         - port: 80
           targetPort: 80
       selector:
         app: nginx
     ```
   - **Explications :**
     - **type: LoadBalancer** indique le type de Service.
     - **ports** spécifie les ports sur lesquels le Service sera exposé.
     - **selector** détermine quels Pods seront exposés par ce Service.

3. **Service de Type NodePort :**
   - Expose le Service sur chaque nœud du cluster à un port statique (le NodePort).
   - Accessible de l'extérieur du cluster en utilisant `<NodeIP>:<NodePort>`.

   **Création du Fichier YAML pour NodePort :**
   - Créez un fichier nommé `nodeport-service.yaml`.
   - Voici un exemple de fichier YAML pour un Service de type `NodePort` :
     ```yaml
     apiVersion: v1
     kind: Service
     metadata:
       name: nginx-nodeport
     spec:
       type: NodePort
       ports:
         - port: 80
           targetPort: 80
           nodePort: 30007
       selector:
         app: nginx
     ```
   - **Explications :**
     - **type: NodePort** spécifie le type de Service.
     - **nodePort** définit le port sur lequel le Service sera accessible depuis l'extérieur du cluster.

4. **Application des Fichiers YAML :**
   - Utilisez `kubectl apply -f loadbalancer-service.yaml` et `kubectl apply -f nodeport-service.yaml` pour créer respectivement les Services.
   - Vérifiez leur statut avec `kubectl get services`.

### Exercices de Prise d'Initiative
- **Test et Comparaison :** Accédez à votre application via les deux types de Services. Notez les différences en termes d'accès et de configuration.
- **Modification des Ports :** Changez les ports dans les fichiers YAML et observez comment cela affecte l'accès aux Services.


- **Exploration de Sélecteurs :** Modifiez les sélecteurs dans vos fichiers de Service pour cibler différents Pods. Cela vous aidera à comprendre comment les Services interagissent avec les Pods.

### Conseils et Bonnes Pratiques
- **Nommage Consistant :** Assurez-vous que les `labels` dans vos fichiers de Deployment correspondent aux `selectors` dans vos fichiers de Service. C'est crucial pour que les Services dirigent le trafic vers les bons Pods.
- **Gestion des Ports :** Pour les Services de type `NodePort`, Kubernetes attribue un port par défaut si `nodePort` n'est pas spécifié. Assurez-vous que le port que vous choisissez ne rentre pas en conflit avec d'autres services sur vos nœuds.
- **Sécurité :** Lors de l'exposition d'applications sur Internet, pensez à la sécurité. Les Services de type `LoadBalancer` peuvent nécessiter des configurations supplémentaires pour la sécurité, comme des pare-feu ou des règles d'ACL.

---

Ces activités pratiques vous fournissent une compréhension approfondie de la manière d'exposer des applications dans un environnement Kubernetes à l'aide de Services. Chaque type de Service a ses propres cas d'utilisation et caractéristiques. En pratiquant ces configurations, vous serez mieux préparé pour gérer l'exposition des applications dans vos futurs projets Kubernetes. Bonne exploration ! 🚀💻🌐