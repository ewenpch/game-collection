# 🎮 Game Collection

Une application web permettant aux utilisateurs de gérer leur bibliothèque de jeux vidéo, de suivre leurs parties et de se comparer aux autres via un leaderboard.

## Aperçu

Game Collection est un projet réalisé dans le cadre d'études. Il permet à chaque utilisateur de créer un compte, d'ajouter des jeux à sa collection personnelle, de consulter un catalogue de jeux et de se mesurer aux autres joueurs via un classement.

## Fonctionnalités

- **Authentification** — Inscription et connexion avec gestion de session
- **Catalogue de jeux** — Parcourir et rechercher des jeux (ex : `?search=minecraft`)
- **Bibliothèque personnelle** — Ajouter des jeux à sa propre collection
- **Gestion des jeux** — Ajouter et modifier des jeux dans le catalogue
- **Profil utilisateur** — Mettre à jour ses informations personnelles
- **Leaderboard** — Classement des joueurs

## Stack technique

| Couche | Technologie |
|--------|-------------|
| Backend | PHP (architecture MVC maison) |
| Frontend | CSS |
| Base de données | MySQL / MariaDB |
| Dépendances | [vlucas/phpdotenv](https://github.com/vlucas/phpdotenv) ^5.6 |
| Autoload | Composer (PSR-4) |
| Serveur | Apache (`.htaccess`) |

## Structure du projet

```
game-collection/
├── controllers/         # Logique métier (GameController, LoginController, etc.)
├── models/              # Accès aux données (Game, User, UserGame)
├── views/               # Templates HTML/PHP
├── assets/              # CSS, images, fichiers statiques
├── .github/workflows/   # CI/CD GitHub Actions
├── index.php            # Point d'entrée + routeur
├── composer.json
└── .env.exemple
```

## Installation

### Prérequis

- PHP >= 8.0
- Composer
- Un serveur MySQL / MariaDB
- Apache avec `mod_rewrite` activé

### Étapes

**1. Cloner le dépôt**

```bash
git clone https://github.com/ewenpch/game-collection.git
cd game-collection
```

**2. Installer les dépendances**

```bash
composer install
```

**3. Configurer l'environnement**

Copier le fichier d'exemple et renseigner vos paramètres de base de données :

```bash
cp .env.exemple .env
```

```env
DB_HOST='localhost'
DB_PORT='3306'
DB_NAME='game_collection'
DB_USER='votre_utilisateur'
DB_PASSWORD='votre_mot_de_passe'
```

**4. Configurer le serveur Apache**

S'assurer que `mod_rewrite` est activé et que le `DocumentRoot` pointe vers le dossier du projet. Le fichier `.htaccess` gère la réécriture des URLs vers `index.php`.

**5. Créer la base de données**

Créer une base de données correspondant à `DB_NAME` et importer le schéma SQL si disponible.

**6. Lancer l'application**

Accéder à l'application via votre navigateur : `http://localhost/`

## Routes disponibles

| Route | Description |
|-------|-------------|
| `GET /` | Page de connexion |
| `POST /login` | Traitement de la connexion |
| `GET/POST /register` | Inscription |
| `GET /home` | Page d'accueil |
| `GET /games` | Catalogue des jeux |
| `POST /add_game` | Ajouter un jeu au catalogue |
| `POST /modify_game` | Modifier un jeu |
| `POST /add_to_library` | Ajouter un jeu à sa bibliothèque |
| `GET/POST /profile` | Profil utilisateur |
| `GET /leaderboard` | Classement des joueurs |
