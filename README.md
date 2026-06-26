# Recipe Management System (Version 2)

## Project Vision

The Recipe Management System is a web application that enables users to create, organize, manage, and publish their personal recipes.

The application consists of two distinct areas:

1. **Private Management Area** – authenticated users manage their own recipes.
2. **Public Publishing Area** – users can choose to publish recipes and share them with anyone through a public URL.

The project aims to demonstrate modern software engineering practices, including layered architecture, authentication and authorization, relational database design, Entity Framework Core, and clean application structure.

---

# Technology Stack

## Backend

* ASP.NET Core MVC
* C#
* ASP.NET Core Identity
* OAuth/OpenID Connect (Google Sign-In initially)
* Entity Framework Core
* LINQ

---

## Frontend

* Razor Views
* Bootstrap 5
* Minimal JavaScript

The focus of the project is backend architecture rather than frontend frameworks.

---

## Database

* SQL Server
* EF Core Code First
* EF Core Migrations

No handwritten SQL for normal CRUD operations.

---

# Application Architecture

The application will follow a conventional **N-Tier Architecture**.

```text
Presentation Layer
(Razor Views)

        │

Controllers

        │

Service Layer
(Business Logic)

        │

Repository Layer
(Data Access)

        │

Entity Framework Core

        │

SQL Server
```

Each layer has a clearly defined responsibility.

---

# Authentication

Authentication will use a third-party identity provider.

Initially:

* Google Sign-In

Future providers could include:

* Microsoft
* GitHub

Passwords will **not** be stored by the application.

---

# Authorization

Every user owns their own recipes.

The system will enforce:

* Users may only edit their own recipes.
* Users may only delete their own recipes.
* Users may only view their private recipes.
* Anonymous visitors cannot access the management area.

Authorization will be enforced on the server.

---

# Core Features

## User Management

* Login
* Logout
* Profile

---

## Recipe Management

Authenticated users can:

* Create recipes
* View recipes
* Edit recipes
* Delete recipes

---

## Recipe Organization

Recipes may include:

* Category
* Ingredients
* Instructions
* Preparation time
* Servings
* Notes

Potential future additions:

* Tags
* Difficulty
* Images

---

## Search

Search recipes by:

* Title
* Ingredient
* Category
* Tags

Implemented with LINQ.

---

## Sorting

Examples:

* Alphabetical
* Recently created
* Recently updated

---

## Filtering

Examples:

* Category
* Favorites
* Tags

---

# Public Recipe Publishing

This is one of the defining features of the application.

A user may choose to publish a recipe.

Published recipes become accessible through a public URL.

Example:

```text
https://recipes.example.com/r/X7QK3Lp9
```

Visitors do **not** need an account.

The public page is intentionally simple:

* Recipe title
* Ingredients
* Instructions
* Preparation information

No editing.

No navigation for management.

No login required.

---

# Recipe Visibility

Every recipe has a visibility state.

**Private**

* Only the owner can access it.

**Public**

* Anyone with the link may view it.

Only the owner may change a recipe's visibility.

---

# Suggested Domain Model

```text
User

    │

    ├──────────── Recipe

    │                 │

    │                 ├──────── Category

    │                 │

    │                 ├──────── RecipeIngredient

    │                 │                │

    │                 │                │

    │                 │          Ingredient

    │                 │

    │                 └──────── RecipeTag (optional)

    │                                   │

    │                                   │

    │                                  Tag
```

This model demonstrates proper relational database design while remaining manageable for a student project.

---

# Design Patterns

The project will naturally make use of several common software engineering patterns.

* MVC
* Repository Pattern
* Service Layer
* Dependency Injection
* Unit of Work (through EF Core DbContext)

---

# Course Topics Covered

| Topic                 | Included |
| --------------------- | -------- |
| C#                    | ✅        |
| ASP.NET Core MVC      | ✅        |
| N-Tier Architecture   | ✅        |
| SQL Server            | ✅        |
| Entity Framework Core | ✅        |
| LINQ                  | ✅        |
| Authentication        | ✅        |
| Authorization         | ✅        |
| Design Patterns       | ✅        |
| UML                   | ✅        |

---

# Stretch Goals

These features will only be implemented if time permits.

* Recipe images
* Favorites
* Shopping list generation
* Nutrition information
* Export recipes (PDF/JSON/XML)
* Meal planner
* Admin dashboard

---

# Project Philosophy

This project is **not** intended to be just another CRUD application.

Its goal is to demonstrate the design and implementation of a modern web application using industry-standard technologies and software engineering principles. While the application domain is recipe management, the emphasis is on clean architecture, maintainability, security, and a well-designed user experience.

---

# Guiding Principle

> **Build a small application as if it were going to be used by real people.**

This mindset influences every architectural decision. It leads to external authentication instead of homemade passwords, proper authorization instead of trusting the client, layered architecture instead of putting everything in controllers, and a public sharing feature that makes the application genuinely useful.

The application should not merely satisfy the course requirements—it should be designed as a production-quality project that demonstrates sound software engineering practices and can confidently be presented as part of a professional portfolio.
