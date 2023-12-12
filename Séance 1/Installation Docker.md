# Activité Pratique : Installation et Découverte de Docker

## Partie Théorique : Qu'est-ce que Docker ?

### Objectifs
- Comprendre ce qu'est Docker et son rôle dans l'écosystème DevOps.
- Saisir les concepts de base liés aux conteneurs.

### Contenu

1. **Introduction à Docker :**
   - **Définition :** Docker est une plateforme open source qui permet de développer, déployer et exécuter des applications dans des conteneurs.
   - **Conteneurs vs Machines Virtuelles :** Les conteneurs sont plus légers, plus rapides et plus efficaces que les machines virtuelles traditionnelles car ils partagent le même système d'exploitation hôte et isolent les applications entre elles.

2. **Concepts Clés :**
   - **Images Docker :** Modèles immuables utilisés pour créer des conteneurs.
   - **Conteneurs Docker :** Instances exécutables d'une image, isolant l'application et ses dépendances.
   - **Docker Hub :** Répertoire public de Docker contenant une multitude d'images préconçues.

3. **Avantages de Docker :**
   - **Portabilité :** Les applications conteneurisées peuvent s'exécuter de manière cohérente sur différents environnements.
   - **Rapidité :** Création, déploiement et redimensionnement rapides des conteneurs.
   - **Isolation :** Les conteneurs fonctionnent de manière isolée, ce qui réduit les conflits entre les applications.

## Partie Pratique : Installation et Exploration de Docker

### Objectifs
- Installer Docker sur votre machine.
- Se familiariser avec les commandes de base de Docker.

### Étapes

1. **Installation de Docker :**
   - Rendez-vous sur [Docker Hub](https://hub.docker.com/).
   - Choisissez votre système d'exploitation (Windows, MacOS, Linux) et suivez les instructions d'installation.
   - **Validation :** Ouvrez un terminal et tapez `docker --version` pour confirmer l'installation.

2. **Exécution du Premier Conteneur :**
   - Dans le terminal, tapez `docker run hello-world`.
   - Cette commande télécharge une image de test et exécute un conteneur qui affiche un message.

3. **Téléchargement et Exécution d'une Image :**
   - Téléchargez une image (par exemple, Ubuntu) : `docker pull ubuntu`.
   - Lancez un conteneur basé sur cette image : `docker run -it ubuntu`.

4. **Exploration des Commandes de Base :**
   - Liste des conteneurs actifs : `docker ps`.
   - Liste de toutes les images : `docker images`.
   - Arrêt d'un conteneur : `docker stop [CONTAINER_ID]`.

### Note Finale 🌟
Docker est un outil puissant qui offre une grande flexibilité et efficacité dans le développement et le déploiement d'applications. Prenez le temps d'expérimenter avec différents conteneurs et images pour mieux comprendre son potentiel. Amusez-vous bien ! 💻🐳

---

Cette activité vous a initié aux bases de Docker. Dans les prochaines sessions, nous explorerons des fonctionnalités plus avancées et intégrerons Docker dans des workflows DevOps plus complexes. Préparez-vous à plonger encore plus profondément ! 🚀🛠️