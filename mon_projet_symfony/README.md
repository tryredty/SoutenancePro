# SoutenancePro

Application de gestion des soutenances de fin d'études pour l'iP Net Institute of Technology.

## Prérequis

- PHP 8.1 ou supérieur
- Composer
- Symfony CLI (recommandé)
- Une base de données PostgreSQL ou MySQL
- Docker et Docker Compose (optionnel)

## Installation

1. Installer les dépendances :

```bash
composer install
```

2. Configurer l'environnement :

```bash
copy .env .env.local
```

Puis ajuster la variable de connexion à la base de données dans le fichier `.env.local` :

```env
DATABASE_URL="postgresql://app:!ChangeMe!@127.0.0.1:5432/app?serverVersion=16&charset=utf8"
```

3. Démarrer la base de données si vous utilisez Docker :

```bash
docker compose up -d database
```

4. Créer la base de données :

```bash
php bin/console doctrine:database:create
```

5. Appliquer les migrations :

```bash
php bin/console doctrine:migrations:migrate
```

6. (Optionnel) Charger des données de test :

```bash
php bin/console app:create-test-users
```

## Lancement du projet

### Option 1 : Symfony CLI

```bash
symfony server:start --no-tls
```

Puis ouvrir :

```text
http://127.0.0.1:8000
```

### Option 2 : Serveur PHP intégré

```bash
php -S 127.0.0.1:8000 -t public
```

## Comptes de test

- Administrateur : admin@ipnet.com / admin123
- Enseignant : teacher1@ipnet.com / teacher123

## Fonctionnalités

- Gestion des étudiants
- Gestion des enseignants
- Gestion des salles de classe
- Planification des soutenances
- Logique anti-collision
- Tableau de bord différent selon le rôle

## Rôles

- ROLE_ADMIN : accès complet
- ROLE_TEACHER : accès au tableau de bord enseignant et à ses soutenances

## Commandes utiles

```bash
php bin/console cache:clear
php bin/phpunit
```

## Technologies

- Symfony 6.4
- PHP 8.1+
- Doctrine ORM
- Twig