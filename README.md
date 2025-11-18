Sistema Web de Control de Gastos

Aplicación web diseñada para gestionar ingresos, gastos y categorías personalizadas, permitiendo a los usuarios llevar un control financiero completo y organizado.
La base de datos está construida en PostgreSQL y estructurada para soportar escalabilidad, múltiples usuarios y análisis futuros.

📌 Características principales

Registro y autenticación de usuarios.

Gestión de categorías de gastos y categorías de ingresos (incluye opciones por defecto y estados).

Registro detallado de gastos y ingresos con fecha, descripción, etiquetas y moneda.

Control de presupuestos mensuales por categoría.

Soporte multiusuario (cada usuario solo ve sus datos).

Base de datos optimizada con llaves foráneas, normalización y relaciones claras.

🗄️ Modelo de Base de Datos (PostgreSQL)

La base de datos se compone de las siguientes tablas:

🔹 USERS

Guarda la información principal del usuario.
Campos relevantes:

user_id (PK)

first_name, last_name

email

password_hash

phone

currency

🔹 EXPENSE_CATEGORIES

Categorías de gastos definidas por el usuario o preconfiguradas.

expense_category_id (PK)

name, description, icon

is_default

monthly_budget

is_active

user_id (FK → USERS)

🔹 INCOME_CATEGORIES

Categorías de ingresos.

income_category_id (PK)

name, description, icon

is_recurring

user_id (FK → USERS)

🔹 EXPENSES

Registro detallado de gastos.

expense_id (PK)

amount, currency

expense_date

description

tags

user_id (FK → USERS)

expense_category_id (FK → EXPENSE_CATEGORIES)

🔹 INCOMES

Registro de ingresos del usuario.

income_id (PK)

amount, currency

income_date

description

source

tags

user_id (FK → USERS)

income_category_id (FK → INCOME_CATEGORIES)
