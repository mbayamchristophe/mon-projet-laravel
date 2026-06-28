# Gestion de Boutique - Projet Laravel (GI2 2025-2026)

Bienvenue dans le système de gestion commerciale de la **Boutique de Monsieur Ali**. Ce projet Laravel permet de gérer les clients, le catalogue de produits, les stocks et la facturation.

##  Auteur du projet
- **NOM** : MBAYAM
- **PRENOM** : CHRISTOPHE
- **ANNEE** : 2026
- **NIVEAU** : GI2



## Table des matières
1. [Prérequis](#prérequis)
2. [Installation sur Windows (XAMPP)](#installation-sur-windows-xampp)
3. [Installation sur Linux (Ubuntu)](#installation-sur-linux-ubuntu)
4. [Résolution des erreurs courantes](#résolution-des-erreurs-courantes)
5. [Fonctionnalités du projet](#fonctionnalités-du-projet)


## Prérequis
- **PHP** : version 8.2 ou supérieure (impératif)
- **Composer** : Gestionnaire de dépendances PHP
- **Extensions PHP requises** : `php-sqlite3`, `php-gd`, `php-xml`, `php-mbstring`, `php-curl`
- **Serveur Web** : XAMPP (Windows) ou Apache/Nginx (Linux)


## Installation sur Windows (XAMPP)

1. **Décompression** : Placez le dossier `ges_boutique` dans `C:\xampp\htdocs\`.
2. **Terminal** : Ouvrez l'invité de commande (CMD) ou PowerShell dans ce dossier.
3. **Dépendances** :
   ```bash
   composer install
   ```
4. **Configuration** :
   - Renommez `.env.example` en `.env` (si nécessaire).
   - Ouvrez `.env` et vérifiez que `DB_CONNECTION=sqlite`.
5. **Initialisation** :
   ```bash
   php artisan key:generate
   php artisan migrate:fresh --seed
   ```
6. **Lancement** : Tapez `php artisan serve` et allez sur `http://127.0.0.1:8000`.

---

## Installation sur Linux (Ubuntu)

1. **Permissions** : Déplacez le projet dans `/var/www/html/` et donnez les droits :
   ```bash
   sudo chown -R www-data:www-data /var/www/html/ges_boutique
   sudo chmod -R 775 /var/www/html/ges_boutique/storage /var/www/html/ges_boutique/bootstrap/cache
   ```
2. **Installation des outils** :
   ```bash
   sudo apt update
   sudo apt install php8.2 php8.2-sqlite3 php8.2-xml php8.2-curl php8.2-mbstring composer
   ```
3. **Dépendances & Base de données** :
   ```bash
   composer install
   php artisan key:generate
   php artisan migrate:fresh --seed
   ```
4. **Apache** : Créez un VirtualHost pointant vers le dossier `/public` du projet.

---

## Résolution des erreurs courantes

### 1. Erreur : "PHP version mismatch" ou "Version de PHP incorrecte"
- **Cause** : Vous utilisez une version trop ancienne (ex: 7.4).
- **Solution** : Mettez à jour PHP vers la version 8.2+. Sur Windows, téléchargez la dernière version de XAMPP. Sur Ubuntu : `sudo apt install php8.2`.

### 2. Erreur : "SQLSTATE[HY000]: General error: 1 no such table"
- **Cause** : La base de données n'est pas initialisée.
- **Solution** : Lancez `php artisan migrate`. Si le fichier `database.sqlite` manque, créez-le : `touch database/database.sqlite`.

### 3. Erreur : "Unique constraint failed: clients.email"
- **Cause** : Vous tentez d'insérer deux fois le même client (via le seed).
- **Solution** : Utilisez `php artisan migrate:fresh --seed` pour vider et repeupler proprement.

### 4. Erreur : "Target class [ClientController] does not exist"
- **Cause** : Problème de namespace ou fichier manquant.
- **Solution** : Vérifiez que les fichiers sont bien dans `app/Http/Controllers/`. Lancez `composer dump-autoload`.

### 5. Erreur : "The stream or file .../logs/laravel.log could not be opened"
- **Cause** : Problème de permissions sur Linux.
- **Solution** : `sudo chmod -R 777 storage`.



## Fonctionnalités du projet
- **Accueil personnalisé** : Tableau de bord "Boutique Ali".
- **Gestion Clients** : CRUD complet (Ajout, Lecture, Modification, Suppression).
- **Catalogue Produits** : Gestion automatique des stocks (décrémentation à la vente, incrémentation à l'annulation).
- **Facturation** : Génération de factures professionnelles prêtes à l'impression.
- **Code Commenté** : Chaque contrôleur et modèle contient des explications en français pour faciliter l'apprentissage.

---
*Réalisé pour Monsieur Ali - Session 2025-2026*
