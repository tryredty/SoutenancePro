# Projet Symfony - Gestion des soutenances

Ce dépôt contient l'application Symfony de gestion des soutenances de fin d'études.

## Prérequis

Avant de lancer le projet, assurez-vous d'avoir installé :

- PHP 8.1 ou supérieur
- Composer
- Symfony CLI (recommandé)
- Docker et Docker Compose (si vous souhaitez utiliser la base de données via conteneur)
- Git

## Installation

1. Se placer dans le dossier du projet :

```bash
cd mon_projet_symfony
```

2. Installer les dépendances PHP :

```bash
composer install
```

3. Configurer l'environnement :

Copiez le fichier d'environnement puis modifiez la variable de connexion à la base de données :

```bash
copy .env .env.local
```

Exemple de configuration avec PostgreSQL :

```env
DATABASE_URL="postgresql://app:!ChangeMe!@127.0.0.1:5432/app?serverVersion=16&charset=utf8"
```

4. Démarrer la base de données (si vous utilisez Docker) :

```bash
docker compose up -d database
```

5. Créer la base de données :

```bash
php bin/console doctrine:database:create
```

6. Appliquer les migrations :

```bash
php bin/console doctrine:migrations:migrate
```

7. (Optionnel) Créer des données de test :

```bash
php bin/console app:create-test-users
```

## Commandes de lancement

### Avec Symfony CLI

```bash
symfony server:start --no-tls
```

Puis ouvrez l'adresse suivante dans votre navigateur :

```text
http://127.0.0.1:8000
```

### Sans Symfony CLI

```bash
php -S 127.0.0.1:8000 -t public
```

## Comptes de test

Si vous avez exécuté la commande ci-dessus, vous pouvez vous connecter avec :

- Administrateur : admin@ipnet.com / admin123
- Enseignant : teacher1@ipnet.com / teacher123

## Commandes utiles

- Vider le cache :

```bash
php bin/console cache:clear
```

- Exécuter les tests :

```bash
php bin/phpunit
```

## Structure du projet

- src/ : logique applicative et entités
- templates/ : vues Twig
- config/ : configuration Symfony
- migrations/ : migrations Doctrine
- public/ : point d'entrée web
