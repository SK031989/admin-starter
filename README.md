<div align="center">

# 🚀 adminStarter

**Enterprise-Ready Modular SaaS & Admin Starter Kit built with Laravel 12, Spatie Roles, Multi-Tenancy & Dynamic Module Builder**

[![Laravel 12](https://img.shields.io/badge/Laravel-12.x-FF2D20?style=flat-square&logo=laravel&logoColor=white)](https://laravel.com)
[![PHP 8.2+](https://img.shields.io/badge/PHP-^8.2-777BB4?style=flat-square&logo=php&logoColor=white)](https://php.net)
[![Tailwind CSS v4](https://img.shields.io/badge/TailwindCSS-v4.0-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)](https://tailwindcss.com)
[![Vite 7](https://img.shields.io/badge/Vite-v7.0-646CFF?style=flat-square&logo=vite&logoColor=white)](https://vitejs.dev)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)

[Features](#-key-features) • [Tech Stack](#-technology-stack) • [Quick Start](#-quick-start--installation) • [Default Credentials](#-default-credentials) • [Modules Architecture](#-modules-architecture) • [Routes](#-routes-overview) • [Artisan Commands](#-cli--artisan-commands)

---

</div>

## 📖 Overview

**adminStarter** is a modern, production-ready, modular admin starter kit and multi-tenant SaaS foundation built on **Laravel 12**. Engineered with a decoupled **Modular Monolith** architecture (`nwidart/laravel-modules`), it provides enterprise authentication, dynamic low-code module generation, multi-tenant data scoping, role-based access control (RBAC), an administrative control panel, and a multi-theme marketing engine right out of the box.

---

## ✨ Key Features

### 🔐 1. Authentication & User Management (`Modules/Auth`)
* **Complete Auth Suite**: Login, multi-tenant registration, email verification, password reset, account deletion.
* **Role-Based Access Control (RBAC)**: Integrated with **Spatie Laravel-Permission** (`Super Admin`, `Tenant Admin`, `User`).
* **Multi-Tenant Scoping**: Built-in `tenant_id` handling and `HasTenantAuth` trait.
* **Security Guarding**: `StrongPasswordRule` validator and `VerifyUserStatus` middleware (handles pending/active/suspended states).
* **Activity & Device Logging**: Tracks IP addresses, browsers, platforms, login attempts, and timestamps in `auth_login_activities`.
* **Profile Management Portal**: Profile info updates, password changes, avatar uploads/removals, and account termination modal.
* **REST API & Sanctum Tokens**: Token generation, inspection, and revocation routes (`/api/v1/auth/*`).

### ⚡ 2. Dynamic Low-Code Module Builder (`Modules/ModuleBuilder`)
* **Visual Schema Designer**: Define custom data modules (e.g., *Projects*, *Invoices*, *Employees*) with zero initial boilerplate.
* **13 Rich Field Types**: `text`, `textarea`, `number`, `email`, `password`, `date`, `datetime`, `select`, `radio`, `checkbox`, `file`, `image`, `boolean`.
* **Automated Code Generator Pipeline**:
  * Eloquent Models & Migration files with multi-tenant scoping.
  * Form Requests with validation rules and type casting.
  * Controllers with full CRUD operations.
  * Blade Views (`index`, `create`, `edit`, `show`) with reusable partials (`form`, `table`, `filters`, `actions`).
  * Dynamic navigation menu items and Spatie CRUD permissions (`{slug}.view`, `{slug}.create`, `{slug}.update`, `{slug}.delete`).
  * Web & API routes.
* **Interactive Drag-to-Reorder**: Reorder field sequences with live AJAX persistence.
* **Queue & Event-Driven Generation**: Asynchronous module code generation via background queues.

### 📊 3. Modern SaaS & Admin Dashboard (`Modules/Dashboard`)
* **Dual Dashboards**: Dedicated UI views for Super Admins (`/admin/dashboard`) and Tenant Users (`/dashboard`).
* **User & Role Administration**: Full management for user accounts and Spatie roles & permissions assignment.
* **System Settings**: Theme switcher, project name, logo, and branding customization portal.
* **Legal & Support Portals**: Pre-built Privacy Policy, Terms of Service, and Support views.

### 🛍️ 4. Pre-Built Sample CRUD Module (`Modules/Product`)
* Production example showcasing standard modular structure with separate Admin (`/admin/products`) and Tenant User (`/products`) controllers, policies, requests, views, and APIs.

### 🎨 5. Multi-Theme Marketing Frontend Engine
* **4 Curated Modern Themes**:
  * 🌌 **Astral** *(Default)*: Sleek, high-contrast, modern SaaS look.
  * ⚡ **Cyber**: Tech-forward cyberpunk styling.
  * ⚪ **Minimal**: Clean, lightweight Scandinavian-inspired typography.
  * 🌑 **Obsidian**: Dark-mode-first glassmorphism aesthetics.
* **Marketing Pages**: Landing / Home (`/`), Features (`/features`), Pricing (`/pricing`), and Contact (`/contact`).
* **Hot-Swappable Theming**: Instant theme switching from the Admin settings dashboard or `config/settings.json`.

---

## 🛠️ Technology Stack

| Layer | Technology |
|---|---|
| **Backend Framework** | [Laravel 12.x](https://laravel.com) (PHP ^8.2) |
| **Modular Architecture** | [nwidart/laravel-modules v12.0](https://github.com/nWidart/laravel-modules) |
| **Authentication & API** | Laravel Session Auth + [Laravel Sanctum v4.3](https://laravel.com/docs/sanctum) |
| **Authorization & RBAC** | [Spatie Laravel-Permission v6.25](https://spatie.be/docs/laravel-permission) |
| **Frontend Styling** | [Tailwind CSS v4.0](https://tailwindcss.com) + Custom Modular Vite Loader |
| **Asset Bundler** | [Vite 7.0](https://vitejs.dev) + `@tailwindcss/vite` |
| **Database** | SQLite (Default) / MySQL / PostgreSQL / MariaDB |
| **Testing** | PHPUnit 11 |

---

## 🚀 Quick Start & Installation

### Prerequisites
* **PHP** >= 8.2 (with `pdo`, `mbstring`, `openssl`, `tokenizer`, `xml`, `ctype`, `json`, `bcmath`, `curl`)
* **Composer** >= 2.x
* **Node.js** >= 18.x & **npm**

### Step-by-Step Setup

1. **Clone the repository:**
   ```bash
   git clone <repository-url> adminStarter
   cd adminStarter
   ```

2. **Install PHP and Node dependencies:**
   ```bash
   composer install
   npm install
   ```

3. **Configure Environment:**
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

4. **Prepare Database & Run Migrations & Seeders:**
   ```bash
   # For SQLite (default)
   touch database/database.sqlite

   # Run all core and modular migrations and seed default users
   php artisan migrate --seed
   ```

5. **Build Assets & Start Development Server:**
   ```bash
   # Option A: Run all dev services concurrently (Server, Queue, Logs, Vite)
   composer run dev

   # Option B: Run standard artisan & vite separately
   php artisan serve
   npm run dev
   ```

6. **Open in your browser:**
   * Landing Page: `http://127.0.0.1:8000`
   * Admin Login: `http://127.0.0.1:8000/admin/login`
   * User Login: `http://127.0.0.1:8000/login`

---

## 👤 Default Credentials

The database seeder (`AuthSeeder`) initializes the following demo accounts:

| Role | Email | Password | Access Level |
|---|---|---|---|
| **Super Admin** | `admin@saas.local` | `AdminPass123!` | Full Admin Panel (`/admin/*`) & Global Settings |
| **Tenant Admin** | `tenant1@saas.local` | `TenantPass123!` | Tenant Dashboard & Organization Admin |
| **Regular User** | `user@saas.local` | `UserPass123!` | Tenant User Portal (`/dashboard`, `/products`) |
| **Pending User** | `pending@saas.local` | `UserPass123!` | Unverified Email Testing Account |

---

## 📂 Project Structure

```
adminStarter/
├── app/                       # Core application controllers, models, providers
│   └── Http/Controllers/
│       └── MarketingController.php  # Multi-theme marketing controller
├── config/                    # Global configurations (marketing, permission, settings, modules)
├── database/                  # Core migrations and root DatabaseSeeder
│   └── migrations/
│   └── seeders/
├── Modules/                   # Modular Monolith Architecture
│   ├── Auth/                  # Authentication, Sanctum API, user policies, login activity
│   │   ├── App/               # Controllers, Requests, Models, Services, Rules, Events, Jobs
│   │   ├── config/            # Auth module configuration
│   │   ├── database/          # Migrations, factories, seeders (AuthSeeder)
│   │   ├── resources/views/   # Login, register, profile, password reset views
│   │   └── routes/            # web.php, api.php, console.php
│   ├── Dashboard/             # Super Admin & User dashboards, roles & settings
│   │   ├── App/Http/          # DashboardController, EnsureUserIsAdmin middleware
│   │   └── resources/views/   # Dashboard, settings, user management, roles CRUD
│   ├── ModuleBuilder/         # Dynamic Visual Code Generator Engine
│   │   ├── App/               # Controllers, Generator Services, Enums, Models
│   │   ├── database/          # Migrations (dynamic_modules, dynamic_fields, etc.)
│   │   └── resources/views/   # Visual module designer & field editor views
│   └── Product/               # Reference CRUD domain module
│       ├── App/               # ProductController, ProductApiController, Product Model
│       └── resources/views/   # Product index, create, edit, show views
├── public/                    # Web root
├── resources/
│   ├── css/                   # Global CSS & Tailwind imports
│   ├── js/                    # Global JavaScript scripts
│   └── views/
│       └── themes/            # Marketing Themes (astral, cyber, minimal, obsidian)
│           ├── astral/
│           ├── cyber/
│           ├── minimal/
│           └── obsidian/
├── routes/
│   ├── web.php                # Root marketing web routes
│   └── console.php            # Root artisan console commands
├── modules_statuses.json      # nwidart module active states
├── vite-module-loader.js      # Automatic asset discovery for all modules
├── vite.config.js             # Vite 7 build configuration with Tailwind v4
└── composer.json              # Dependencies, PSR-4 mapping & composer scripts
```

---

## 🌐 Routes Overview

### 🖥️ Public & Marketing Routes
| Method | URI | Description |
|---|---|---|
| `GET` | `/` | Home / Landing Page (Active Theme) |
| `GET` | `/features` | Product Features Page |
| `GET` | `/pricing` | Pricing Plans Page |
| `GET` | `/contact` | Contact Page |

### 🔐 Authentication Routes (`Modules/Auth`)
| Method | URI | Name | Description |
|---|---|---|---|
| `GET` / `POST` | `/login` | `auth.login` | User Login & Authentication |
| `GET` / `POST` | `/admin/login` | `admin.login` | Super Admin Dedicated Login |
| `POST` | `/auth/logout` | `auth.logout` | User Logout |
| `GET` / `POST` | `/register` | `auth.register` | Tenant User Registration |
| `GET` / `POST` | `/auth/forgot-password` | `auth.password.request` | Password Reset Request |
| `GET` / `POST` | `/auth/reset-password/{token}` | `auth.password.reset` | Password Reset Form & Action |
| `GET` | `/auth/verify-email` | `auth.verify.notice` | Email Verification Notice |
| `GET` / `PUT` | `/profile` | `auth.profile.edit` | Profile Details & Avatar Management |
| `PUT` | `/profile/password` | `auth.profile.password.update`| Profile Password Upgrade |
| `DELETE` | `/profile` | `auth.profile.destroy` | Account Termination |

### 🛡️ Super Admin Control Panel (`Modules/Dashboard`)
| Method | URI | Description |
|---|---|---|
| `GET` | `/admin/dashboard` | Super Admin Metrics & Dashboard |
| `GET` | `/admin/users` | User Accounts Directory |
| `PUT` | `/admin/users/{user}/role` | Assign Role to User |
| `GET` / `POST` | `/admin/roles` | Spatie Roles & Permissions Management |
| `GET` / `POST` | `/admin/settings` | System & Theme Settings |

### ⚡ Low-Code Module Builder (`Modules/ModuleBuilder`)
| Method | URI | Description |
|---|---|---|
| `GET` / `POST` | `/module-builder` | List & Create Dynamic Modules |
| `GET` / `PUT` / `DELETE`| `/module-builder/{id}` | Module Schema Inspection & Updates |
| `POST` | `/module-builder/{id}/fields` | Add Fields to Module |
| `POST` | `/module-builder/{id}/fields/reorder` | Drag-to-Reorder Fields (AJAX) |
| `POST` | `/module-builder/{id}/generate` | Generate Code (Models, Migrations, Views, Controllers) |
| `GET` | `/module-builder/{id}/preview` | Preview Generated Schema & Code |

### 📡 Sanctum API Endpoints
| Method | URI | Description |
|---|---|---|
| `POST` | `/api/v1/auth/login` | Generate Sanctum Bearer Token |
| `GET` | `/api/v1/auth/user` | Fetch Current Authenticated User |
| `POST` | `/api/v1/auth/logout` | Revoke Sanctum Token |
| `GET` / `POST` | `/api/v1/module-builder` | Module Builder REST API |
| `GET` / `POST` | `/api/v1/products` | Product Module REST API |

---

## 💻 CLI & Artisan Commands

### Module Management (`nwidart/laravel-modules`)
```bash
# List all registered modules
php artisan module:list

# Enable or disable a module
php artisan module:enable <ModuleName>
php artisan module:disable <ModuleName>

# Run migrations for a specific module
php artisan module:migrate Auth
php artisan module:migrate ModuleBuilder

# Run seeders for a specific module
php artisan module:seed Auth --class=AuthSeeder
php artisan module:seed ModuleBuilder --class=ModuleBuilderSeeder
```

### Module Builder Commands
```bash
# Generate full CRUD code for a dynamic module by slug
php artisan module-builder:generate <module-slug>

# List all defined dynamic modules and generation status
php artisan module-builder:list
```

### Auth & User Utilities
```bash
# Display all registered accounts in terminal table
php artisan auth:list-users

# Create a new administrator account interactively
php artisan auth:create-admin "Admin Name" "admin@example.com" "SecurePass123!"
```

---

## 🧪 Testing & Code Quality

Run tests using PHPUnit:
```bash
# Run all application and module tests
php artisan test

# Run tests via Composer script
composer run test
```

Format code with Laravel Pint:
```bash
./vendor/bin/pint
```

---

## 📄 License

This project is open-sourced software licensed under the [MIT License](LICENSE).
