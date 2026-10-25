# Culinary Atlas
### A Relational Database for Indian Traditional Cuisine and Culinary Heritage

**Culinary Atlas** is a MySQL-based relational database project designed to organize and preserve information about India's traditional cuisines, regional dishes, ingredients, recipes and culinary heritage.

The project demonstrates how relational database concepts can be used to store, organize, retrieve and manage interconnected culinary information through structured SQL queries.

---

## 📌 Project Overview

India has a diverse culinary heritage, with every region offering unique dishes, ingredients, cooking methods and food traditions.

Culinary Atlas provides a structured database to organize this information and make it easier to explore the relationship between Indian states, regional cuisines, traditional dishes, their ingredients and cultural significance.

The database uses a relational model with primary keys, foreign keys, constraints, joins and stored procedures to maintain relationships and retrieve meaningful information.

## 🎯 Objectives

- Organize information about Indian states and their regional cuisines.
- Maintain a structured collection of traditional Indian dishes.
- Store ingredients and their quantities for individual dishes.
- Maintain recipe information, including preparation time and cooking methods.
- Document the cultural and traditional significance of dishes.
- Demonstrate relational database concepts through practical SQL operations.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| MySQL 8.0+ | Relational database management |
| SQL | Database creation, manipulation and retrieval |
| Microsoft Excel | Dataset preparation and organization |
| Draw.io | Entity Relationship Diagram |
| Git & GitHub | Version control and project hosting |

## 🗄️ Database Architecture

The project consists of **7 relational tables**, each containing 6 attributes.

| Table | Description |
|---|---|
| `states` | Stores Indian state details, capitals, languages and geographical information. |
| `cuisines` | Stores regional cuisine information associated with states. |
| `dishes` | Contains traditional dishes, categories, food types and occasions. |
| `ingredients` | Stores ingredient names, categories, units and other details. |
| `dish_ingredients` | Connects dishes with their ingredients, quantities and preparation forms. |
| `recipes` | Stores preparation time, cooking time, servings and cooking methods. |
| `heritage_notes` | Documents cultural significance and traditional serving information. |

### Entity Relationships

- **STATES → CUISINES:** One-to-Many
- **CUISINES → DISHES:** One-to-Many
- **DISHES → INGREDIENTS:** Many-to-Many, implemented through `dish_ingredients`.
- **DISHES → RECIPES:** One-to-One
- **DISHES → HERITAGE_NOTES:** One-to-One

The `dish_ingredients` table acts as a junction (bridge) table to resolve the many-to-many relationship between dishes and ingredients.

## 📊 Dataset Details

The database contains 165 records distributed across seven tables.

| Table | Records |
|---|---:|
| STATES | 15 |
| CUISINES | 15 |
| DISHES | 15 |
| INGREDIENTS | 27 |
| DISH_INGREDIENTS | 63 |
| RECIPES | 15 |
| HERITAGE_NOTES | 15 |
| **Total** | **165** |

The dataset covers representative traditional dishes from 15 Indian states.

## ✨ Key Features

### 1. Regional Cuisine Exploration
Explore Indian states and their associated regional cuisines.

### 2. Dish Information Retrieval
Retrieve information about a dish, including its name, category, food type, associated cuisine and state.

### 3. Ingredient Management
Identify the ingredients required for individual dishes, including their quantities, units and preparation forms.

### 4. Recipe Information
Retrieve preparation time, cooking time, servings and cooking methods.

### 5. Culinary Heritage Documentation
Store cultural significance, traditional serving practices and associated festivals or occasions.

### 6. Stored Procedure
The `GetDishDetails` stored procedure accepts a dish name as input and retrieves information from multiple related tables through a single procedure call.

Example:

```sql
CALL GetDishDetails('Dhokla');
```

The procedure returns four result sets:

1. Basic dish information.
2. Ingredients with quantities.
3. Recipe and cooking method.
4. Cultural and heritage information.

## 💻 Installation and Setup

### Prerequisites

- MySQL Server 8.0.16 or later.
- MySQL command-line client.
- Git (optional, for cloning the repository).

### Step 1: Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

Navigate to the project directory:

```bash
cd Culinary-Atlas
```

### Step 2: Import the Database

Ensure that `Culinary_Atlas_MySQL.sql` is present in the project directory.

Execute:

```bash
mysql -u root -p < Culinary_Atlas_MySQL.sql
```

Enter your MySQL root password when prompted.

This creates the `culinary_atlas` database, its seven tables and inserts the dataset.

**Note:** The SQL setup script drops and recreates tables with matching names. Back up existing project data before rerunning it.

### Step 3: Access the Database

Log in to MySQL:

```bash
mysql -u root -p
```

Select the database:

```sql
USE culinary_atlas;
```

Display all tables:

```sql
SHOW TABLES;
```

### Step 4: Verify the Records

```sql
SELECT COUNT(*) FROM states;
SELECT COUNT(*) FROM cuisines;
SELECT COUNT(*) FROM dishes;
SELECT COUNT(*) FROM ingredients;
SELECT COUNT(*) FROM dish_ingredients;
SELECT COUNT(*) FROM recipes;
SELECT COUNT(*) FROM heritage_notes;
```

## 🔍 Example SQL Queries

### 1. Display All Indian States

```sql
SELECT * FROM states;
```

### 2. Retrieve All Vegetarian Dishes

```sql
SELECT dish_name, food_type
FROM dishes
WHERE food_type = 'Vegetarian';
```

### 3. Retrieve Dishes Along With Their States

```sql
SELECT
    d.dish_name,
    c.cuisine_name,
    s.state_name
FROM dishes d
JOIN cuisines c
    ON d.cuisine_id = c.cuisine_id
JOIN states s
    ON c.state_id = s.state_id;
```

### 4. Retrieve Ingredients for a Specific Dish

```sql
SELECT
    d.dish_name,
    i.ingredient_name,
    di.quantity,
    di.unit
FROM dishes d
JOIN dish_ingredients di
    ON d.dish_id = di.dish_id
JOIN ingredients i
    ON di.ingredient_id = i.ingredient_id
WHERE d.dish_name = 'Dhokla';
```

### 5. Retrieve Dish Details Using the Stored Procedure

```sql
CALL GetDishDetails('Dhokla');
```

**Note:** Create the `GetDishDetails` stored procedure separately after importing the database. Its definition is not included in the current SQL setup script.

## 🧠 DBMS Concepts Demonstrated

This project implements and demonstrates the following database concepts:

- Relational Database Management System (RDBMS).
- Database schema and table creation.
- Primary Key and Foreign Key constraints.
- Composite Primary Keys.
- Referential Integrity.
- One-to-Many and Many-to-Many relationships.
- SQL DDL and DML operations.
- SELECT, WHERE, ORDER BY and DISTINCT.
- Aggregate Functions and GROUP BY.
- INNER JOIN and LEFT JOIN.
- Subqueries.
- Views and Stored Procedures.
- Indexing and database constraints.

## 📁 Project Structure

```text
Culinary-Atlas/
│
├── README.md
│
├── Culinary_Atlas_MySQL.sql
│
├── Culinary_Atlas_Dataset.xlsx
│
└── ER_Diagram/
    └── Culinary_Atlas_ER_Diagram.png
```

*The ER diagram folder will be added once the diagram is finalized.*

## 🚀 Future Enhancements

- Develop a web-based interface for searching traditional Indian dishes.
- Add more regional cuisines and traditional recipes.
- Implement advanced search and filtering functionalities.
- Add user-friendly visualizations for exploring regional food diversity.
- Integrate additional historical and cultural references.

## 👨‍💻 Project Information

**Project Name:** Culinary Atlas

**Domain:** Database Management Systems (DBMS)

**Database:** MySQL

**Project Type:** Academic / Educational Project

**Theme:** Indian Knowledge System (IKS) – Traditional Indian Cuisine and Culinary Heritage

---

*Preserving India's culinary diversity through structured data and relational database technology.*
