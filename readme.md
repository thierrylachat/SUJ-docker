
# Docker

## Préparation de l'environnement de travail

 **1. Installer Linux sur Windows avec WSL** :
Sur Windows, exécuter les commandes nécessaires à l'installation et à la configuration du sous-système linux. Faire en sorte d'installer la dernière distribution d'Ubuntu.

 **2. Utiliser la ligne de commande** :
 Windows : Démarrer Ubuntu afin de finir la configuration et afin d'utiliser le terminal de cet OS.
 Macos : Démarrer un terminal

 Créer un dossier `www` dans le dossier de votre compte utilisateur.

## Docker engine

 **1. Installation et vérification de l'installation** :
Installez Docker sur votre système d'exploitation et vérifiez en ligne de commandes le numéro de version du daemon installé.

 **2. Exécution d'un conteneur simple** :
Depuis le terminal, utilisez la commande `docker run hello-world` pour exécuter un conteneur Docker minimal. Observez le message renvoyé.

 **3. Listing des image** :
 Trouver la commande permettant de lister toutes les images docker présentes sur le système

 **4. Listing des containers** :
 Trouver la commande permettant de lister tous les containers présents sur le système

 **5. Suppression d'une image** :
 Supprimer l'image installée lors de l'exécution de la commande `docker run hello-world`

 **6. Exécution d'un conteneur avec une image spécifique** :
Cherchez l'image du serveur web "Apache" sur DockerHub et démarrez un conteneur à partir de cette image. Ce container devra permettre de démarrer un serveur web afin d'accéder au Vhost <http://localhost:8080>. Celui-ci doit afficher "It Works".

**7. Se connecter au container** :
 En ligne de commandes, se connecter au container.
 Installer l'éditeur de texte nano si celui-ci n'est pas installé dans le container. Créer une page web grâce à l'éditeur de texte `nano` afin d'afficher "I Am the King!!" au lieu de "It Works".

**8. Création d'une image sans Dockerfile** :
 Grâce au container précédent, créer une nouvelle image contenant votre page par défaut, ainsi que nano pré-installé.
 Testez votre image nouvellement créée en démarrant un nouveau container. Vérifiez qu'il s'agit bien de votre image en vous rendant sur le Vhost <http://localhost:8080>.

 **9. Création d'une image avec Dockerfile** :
*Vous allez créer une nouvelle image en utilisant un fichier "dockerfile".*
Dans le dossier `www` de votre compte utilisateur, créez un nouveau dossier `my-project`. Rendez-vous dans ce dossier, et avec une ligne de commande, ouvrez ce dossier avec VSCode.
Créez un fichier `dockerfile` à la racine. Celui-ci doit contenir les éléments nécessaires à la génération d'une image de type `debian`, la dernière. Il devra aussi contenir les instructions permettant d'installer nano dans l'image.
Créez l'image, et démarrez un container à partir de cette image.
Vérifiez le bon fonctionnement de l'éditeur nano, en vous connectant au container.

 **10. Plus loin avec Dockerfile** :
Démarrez votre container à partir de cette image en faisant en sorte de synchroniser votre dossier local, avec le dossier du container ([Bind Mounts](https://docs.docker.com/storage/bind-mounts/#start-a-container-with-a-bind-mount)).
Effectuez une modification du fichier `index.html` depuis le container, puis depuis le dossier local. Constatez la bonne synchronisation du fichier.

## Docker compose

*Un container peut être composé de plusieurs images, un/des volume(s). Docker compose permet de créer des containers embarquant une configuration donnée.*

1. Dans le dossier `www` de votre compte utilisateur, créez un nouveau dossier `my-project-compose`. Démarrez VSCode depuis ce dossier. Créez un fichier `compose.yaml` à la racine.
2. Ajoutez dans ce fichier un service nommé web, permettant d'utiliser l'image `httpd`, la dernière.
3. Vérifiez le bon démarrage et fonctionnement du container depuis le terminal en utilisant `docker compose up`
4. Configurez les ports dans le fichier `compose.yaml` puis vérifiez le bon fonctionnement du serveur web sur l'url `http://localhost:8080/`
5. Dans votre dossier, créez un dossier app, puis créez-y un nouveau fichier html contenant le texte "I am the king of Docker compose".
6. Modifiez le fichier `compose.yaml` afin de créer un nouveau volume qui se synchronisera avec votre dossier `app`. Rechargez votre vhost afin de voir les changements.
7. Configurer les éléments nécessaires à l'exploitation de nano dans le container
