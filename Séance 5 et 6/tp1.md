# Travaux Pratiques : Préparation et Configuration d'un Deployment Kubernetes

## Partie 1 : Comprendre et Configurer un Deployment Kubernetes
**Durée estimée : 1h30**

### Objectifs
- Approfondir la compréhension de la configuration d'un Deployment dans Kubernetes.
- Se familiariser avec la structure et les éléments clés d'un fichier YAML pour Kubernetes.

### Étapes et Détails du Fichier YAML

1. **Sélection de l'Application :**
   - Choisissez une application conteneurisée simple, comme `nginx` ou `httpd`.
   - Assurez-vous que l'image du conteneur est disponible sur un registre public (ex. Docker Hub).

2. **Compréhension de la Structure YAML :**
   - Un fichier YAML pour un Deployment Kubernetes se compose de plusieurs sections clés. Nous allons les explorer à travers un exemple.

3. **Création du Fichier YAML :**
   - Ouvrez votre éditeur de texte et commencez à rédiger le fichier YAML. Voici la structure de base et les explications pour chaque section :
   
     ```yaml
     apiVersion: apps/v1              # La version de l'API Kubernetes utilisée
     kind: Deployment                 # Le type de ressource que vous créez
     metadata:
       name: nginx-deployment         # Le nom du Deployment
     spec:
       replicas: 2                    # Le nombre de réplicas (instances) de l'application
       selector:
         matchLabels:
           app: nginx                # Les étiquettes utilisées pour identifier les Pods
       template:                      # Le template du Pod
         metadata:
           labels:
             app: nginx              # Les étiquettes attribuées aux Pods créés
         spec:
           containers:
           - name: nginx              # Le nom du conteneur dans le Pod
             image: nginx:latest      # L'image du conteneur à utiliser
             ports:
             - containerPort: 80      # Le port sur lequel le conteneur sera exposé
     ```
   
4. **Explication Détaillée :**
   - **apiVersion :** Spécifie la version de l'API Kubernetes utilisée pour créer l'objet.
   - **kind :** Indique le type de l'objet Kubernetes que vous souhaitez créer. Ici, c'est un `Deployment`.
   - **metadata :** Contient des informations comme le `name` du Deployment. Vous pouvez également ajouter des `labels` pour organiser vos ressources.
   - **spec :** Décrit l'état souhaité de l'objet, comme le nombre de réplicas.
   - **selector :** Utilisé pour identifier les Pods que le Deployment doit gérer. Les `labels` des Pods doivent correspondre à ces sélecteurs.
   - **template :** Définit le template des Pods. Inclut les

`metadata` (comme les `labels`) et la `spec` pour les conteneurs dans les Pods.
   - **containers :** Liste des conteneurs à exécuter dans le Pod. Inclut des détails comme le `name` du conteneur, l'`image` à utiliser, et les `ports`.

5. **Application du Fichier YAML :**
   - Enregistrez le fichier avec un nom approprié (ex. `nginx-deployment.yaml`).
   - Utilisez `kubectl apply -f nginx-deployment.yaml` pour créer le Deployment dans votre cluster Kubernetes.
   - Vérifiez le statut avec `kubectl get deployments`.

### Exercices de Prise d'Initiative
- **Modification du Nombre de Réplicas :** Changez le nombre de réplicas dans votre fichier YAML et observez comment Kubernetes adapte le nombre de Pods en conséquence.
- **Changement d'Image de Conteneur :** Modifiez l'image de conteneur (par exemple, passez à une version différente de `nginx`) dans votre fichier YAML et appliquez les modifications. Observez comment le Deployment met à jour les Pods.
- **Ajout de Variables d'Environnement :** Expérimentez en ajoutant des variables d'environnement dans la section `containers` de votre fichier YAML. Par exemple, définissez une variable d'environnement pour configurer le comportement de l'application.

### Conseils et Bonnes Pratiques
- **Nommage Clair :** Utilisez des noms descriptifs pour vos fichiers YAML et les ressources Kubernetes.
- **Validation du YAML :** Utilisez des outils en ligne ou des éditeurs de texte avec support YAML pour valider la syntaxe de votre fichier.
- **Documentation :** Consultez la documentation officielle de Kubernetes pour comprendre les différentes options de configuration.

---

Ce TP vous permettra de maîtriser les bases de la configuration d'un Deployment dans Kubernetes. N'oubliez pas, la pratique est la clé de l'apprentissage, alors n'hésitez pas à expérimenter avec différentes configurations pour voir leur impact en direct. Bon codage ! 🚀💡💻