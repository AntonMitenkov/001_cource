# Моделирование данных: от концепции к реализации

## Уровни моделирования данных

### Conceptual Model (Концептуальная модель)

**Назначение:** Высокоуровневое описание бизнес-сущностей и их связей
без технических деталей.

**Аудитория:** Бизнес-аналитики, product owners, stakeholders.

**Содержание:**
- Основные сущности (Customer, Order, Product)
- Связи между сущностями (Customer places Order, Order contains Product)
- Бизнес-правила (Customer can have multiple Orders)

**Инструменты:** Доски, диаграммы в Miro/Figma, текстовые описания.

**Пример:**

Customer (1) --- places ---> () Order
Order () --- contains ---> (*) Product


### Logical Model (Логическая модель)

**Назначение:** Детализация концептуальной модели с атрибутами, типами
данных и правилами нормализации, но без привязки к конкретной СУБД.

**Аудитория:** Data architects, разработчики.

**Содержание:**
- Атрибуты сущностей (Customer: id, name, email, created_at)
- Типы данных (INTEGER, VARCHAR, TIMESTAMP)
- Primary keys, foreign keys
- Нормализация (3NF обычно)
- Constraints и business rules

**Инструменты:** ERD-редакторы (draw.io, Lucidchart, DataGrip).

**Пример:**

CUSTOMERS
--
customer_id (PK, INT)
name (VARCHAR(100))
email (VARCHAR(255), UNIQUE)
created_at (TIMESTAMP)

ORDERS
--
order_id (PK, INT)
customer_id (FK → CUSTOMERS)
order_date (TIMESTAMP)
status (ENUM: pending, shipped, delivered)



### Physical Model (Физическая модель)

**Назначение:** Реализация логической модели в конкретной СУБД с учётом
производительности и особенностей хранения.

**Аудитория:** DBA, разработчики.

**Содержание:**
- Специфичные для СУБД типы данных (PostgreSQL UUID, JSONB)
- Индексы (B-tree, GIN, GiST)
- Партиционирование таблиц
- Денормализация для производительности
- Storage engines (InnoDB vs MyISAM)
- Compression, partitioning strategies

**Инструменты:** DDL-скрипты, миграции (Flyway, Liquibase),
ORM-схемы.

**Пример:**
```sql
-- PostgreSQL-специфичная реализация
CREATE TABLE customers (
  customer_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name VARCHAR(100) NOT NULL,
  email VARCHAR(255) UNIQUE NOT NULL,
  created_at TIMESTAMPTZ DEFAULT NOW()
);

CREATE INDEX idx_customers_email ON customers(email);
CREATE INDEX idx_customers_created_at ON customers(created_at DESC);
