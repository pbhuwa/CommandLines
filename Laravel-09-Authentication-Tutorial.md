# Laravel 9 Authentication Tutorial

## Table of Contents

- [What is Laravel?](#what-is-laravel)
- [Key Features of Laravel](#key-features-of-laravel)
- [New Features in Laravel 9](#new-features-in-laravel-9)
- [1. Install Laravel Project](#1-install-laravel-project)
- [2. Configure Database Details](#2-configure-database-details)
- [3. Create Auth using Scaffold](#3-create-auth-using-scaffold)
  - [Generate basic scaffolding and login and registration for Bootstrap](#generate-basic-scaffolding-and-login-and-registration-for-bootstrap)
  - [Generate basic scaffolding and login and registration for Vue](#generate-basic-scaffolding-and-login-and-registration-for-vue)
  - [Generate basic scaffolding and login and registration for React](#generate-basic-scaffolding-and-login-and-registration-for-react)
  - [Generate basic scaffolding](#generate-basic-scaffolding)
  - [Generate login/registration scaffolding](#generate-loginregistration-scaffolding)
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

## New Features in Laravel 9

- Minimum PHP Requirement
- New Design for `routes:list`
- Anonymous stub migration
- New Query Builder Interface
- PHP 8 String Functions

Laravel provides a very simple and cool UI package for the easy step of auth scaffolding. Laravel UI composer package provides simple authentication features like login, registration, password reset, email verification, and password confirmation using Bootstrap, React, and Vue.

We need an authentication system for keeping our application private. Making authentication in Laravel is quite easy. It has a built-in solution for authentication and various facilities to customize it according to our requirements. If you are new to Laravel 9, then in this post I'll show you the step-by-step process for making an authentication system in Laravel 9. Let's follow the step-by-step process for making an authentication system in Laravel 9.

## 1. Install Laravel Project

First, open Terminal and run the following command to create a fresh Laravel project:

```bash
composer create-project --prefer-dist laravel/laravel laravel9-auth
```

or, if you have installed the Laravel Installer as a global composer dependency:

```bash
laravel new laravel9-auth
```

## 2. Configure Database Details

After installation, go to the project root directory, open the `.env` file, and set the database details as follows:

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=<DATABASE_NAME>
DB_USERNAME=<DATABASE_USERNAME>
DB_PASSWORD=<DATABASE_PASSWORD>
```

Now run the database migration command:

```bash
php artisan migrate
```

## 3. Create Auth using Scaffold

Now, in this step, we will create auth scaffold commands to create login, register, and dashboard.

```bash
composer require laravel/ui
```

### Generate basic scaffolding and login and registration for Bootstrap

```bash
php artisan ui bootstrap
php artisan ui bootstrap --auth
```

### Generate basic scaffolding and login and registration for Vue

```bash
php artisan ui vue
php artisan ui vue --auth
```

### Generate basic scaffolding and login and registration for React

```bash
php artisan ui react
php artisan ui react --auth
```

### Generate basic scaffolding

```bash
php artisan ui bootstrap
php artisan ui vue
php artisan ui react
```

### Generate login/registration scaffolding

```bash
php artisan ui bootstrap --auth
php artisan ui vue --auth
php artisan ui react --auth
```

## 4. Install NPM Dependencies

Run the following command to install node dependencies and compile CSS and JS files:

```bash
npm install && npm run dev
```

## 5. Test the Authentication System

Now our Laravel 9 Authentication is ready to use. To check if authentication is successfully installed or not, first run the project.

```bash
php artisan serve
```