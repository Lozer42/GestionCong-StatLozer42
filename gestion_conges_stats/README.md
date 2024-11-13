
## Atelier Symfony : Rédaction du README

Votre mission est de rédiger le fichier README de ce dépôt, en y incluant les instructions détaillées pour son déploiement.

# Installation et Configuration Complète

## Prérequis
1. **PHP 8.1 ou plus récent** - Installez PHP via votre gestionnaire de paquets ou téléchargez-le depuis [php.net](https://www.php.net/).
2. **Composer** - Installez [Composer](https://getcomposer.org/download/) pour gérer les dépendances PHP.
3. **Symfony CLI** - Recommandé pour faciliter la gestion du serveur. [Téléchargez ici](https://symfony.com/download).
4. **Base de données (MySQL)** - Installez MySQL et créez une base de données pour le projet.

## Étapes d'Installation

1. **Cloner le projet :**
   ```bash
   git clone https://github.com/ggaillard/gestion_conges_stats.git
   cd gestion_conges_stats

2. **Installer les dépendances**
Installez les dépendances PHP nécessaires avec Composer pour que Symfony et les autres composants fonctionnent correctement.

    ```bash
    composer install
Cette commande télécharge toutes les bibliothèques et packages définis dans composer.json, y compris Symfony.

3. **Configurer les variables d’environnement :**
Créez un fichier .env à partir de .env.example :
    ```bash
    cp .env.example .env
4. **Ouvrez .env et modifiez DATABASE_URL pour votre base de données :**
    ```bash
    DATABASE_URL="mysql://username:password@127.0.0.1:3306/nombase"
5. **Créer la base de données :**
    ```bash
    php bin/console doctrine:database:create
Cette commande crée la base de données spécifiée dans .env.

6. Appliquer les migrations :
    ```bash
    php bin/console doctrine:migrations:migrate
Cela crée les tables nécessaires.

## Lancer le Serveur Symfony

1. Démarrer le serveur :
- Avec Symfony CLI :
```bash
symfony server:start
```

2. Accéder au site : Rendez-vous sur http://localhost:8000.

# Sauvegarde et Restauration de la Base de Données

## Sauvegarde de la Base de Données
1. Utiliser mysqldump pour sauvegarder toutes les données de votre base de données :

```bash
mysqldump -u username -p nombase > sauvegarde.sql
```
Cette commande crée un fichier sauvegarde.sql contenant toute la structure et les données de la base.


2. Vérifier la sauvegarde pour s’assurer qu’elle contient bien toutes les informations :

```bash
less sauvegarde.sql
```

## Restauration de la Base de Données
1. Restaurez la base de données en utilisant le fichier de sauvegarde :

```bash
mysql -u username -p nombase < sauvegarde.sql
```
Cette commande recharge toutes les données dans la base.

2. Vérifiez dans Symfony que les données sont correctement restaurées en lançant le projet et en accédant aux données.