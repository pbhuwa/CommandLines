# Laravel 11 Authentication Tutorial

## Table of Contents

- [What is Laravel?](#what-is-laravel)
- [Key Features of Laravel](#key-features-of-laravel)
- [New Features in Laravel 11](#new-features-in-laravel-11)
- [1. Install Laravel Project](#1-install-laravel-project)
- [2. Configure Database Details](#2-configure-database-details)
- [3. Create Auth using Breeze](#3-create-auth-using-breeze)
- [4. Install NPM Dependencies](#4-install-npm-dependencies)
- [5. Test the Authentication System](#5-test-the-authentication-system)

## What is Laravel?

Laravel is an open-source PHP web application framework with expressive, elegant syntax. It is an MVC framework for building simple to complex web applications using the PHP programming language.

Laravel strictly follows the MVC (Model-View-Controller) architectural pattern. It is known for its beautiful and elegant syntax as a web framework.

## Key Features of Laravel

Some of the main features of Laravel are:

- Eloquent ORM
- Query builder
- Reverse Routing
- Restful Controllers
- Migrations
- Database Seeding
- Unit Testing
- Homestead
- Source code hosted on GitHub and licensed under MIT License.
- Most Starred PHP Framework for custom software development on GitHub.
- Its ability to use all of the new features of PHP sets it apart.
- Friendly online community
- Detailed documentation
- Security

## New Features in Laravel 11

- PHP 8.2 support (minimum requirement).
- Enhanced Routing with group and alias handling.
- Improved Eloquent ORM for more flexibility.
- Updated API resources for better performance.
- Enhanced validation methods.

Laravel 11 uses **Laravel Breeze** as its lightweight authentication starter kit. This provides basic authentication scaffolding with minimal dependencies. Let’s follow the step-by-step guide to set up authentication in Laravel 11.

## 1. Install Laravel Project

First, open your terminal and run the following command to create a new Laravel project:

```bash
composer create-project --prefer-dist laravel/laravel laravel11-auth
```

Or, if you have the Laravel Installer globally installed:

```bash
laravel new laravel11-auth
```

Navigate to the project directory:

```bash
cd laravel11-auth
```

## 2. Configure Database Details

Open the `.env` file located in the root of your project and set up your database connection details:

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=<DATABASE_NAME>
DB_USERNAME=<DATABASE_USERNAME>
DB_PASSWORD=<DATABASE_PASSWORD>
```

Run the migration to create the necessary database tables:

```bash
php artisan migrate
```

## 3. Create Auth using Breeze

Laravel 11 recommends using **Laravel Breeze** for authentication scaffolding. Install Breeze via Composer:

```bash
composer require laravel/breeze --dev
```

Publish the Breeze scaffolding:

```bash
php artisan breeze:install
```

You can also specify the frontend stack during installation (default is Blade):

- **Blade** (Default):  
  ```bash
  php artisan breeze:install
  ```

- **Vue.js**:  
  ```bash
  php artisan breeze:install vue
  ```

- **React.js**:  
  ```bash
  php artisan breeze:install react
  ```

Run the migrations and install dependencies:

```bash
php artisan migrate
npm install
npm run build
```

## 4. Install NPM Dependencies

If not already done during Breeze setup, run the following commands to install and compile frontend assets:

```bash
npm install
npm run build
```

> Laravel 11 uses Vite as the default build tool, ensuring faster development builds and optimizations.

## 5. Test the Authentication System

Run the local development server to test the authentication system:

```bash
php artisan serve
```

Open your browser and navigate to `http://127.0.0.1:8000`. You should see the authentication pages (login, register, etc.) fully functional.

Congratulations! You now have a basic authentication system set up in **Laravel 11**.

> [!NOTE] 
> This tutorial is adapted for Laravel 11 using Laravel Breeze as the recommended lightweight authentication starter kit

This tutorial uses the modern Laravel 11 structure and **Laravel Breeze** for authentication, which is simpler and more lightweight than Laravel UI. If you need anything more specific (like integrating additional stacks), let me know!