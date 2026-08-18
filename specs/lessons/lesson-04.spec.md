---
id: lesson-04
title: "Архитектура данных и выбор СУБД."
status: draft
duration: 80
domain: "маркетплейс / финтех / каршеринг / телемедицина"
depends_on:
  - lesson-03
next:
  - lesson-05
required_skills:
  - ...
---
Обнови specs/lessons/lesson-04.spec.md.

Тема:
"Архитектура данных и выбор СУБД".

### обязательные концепции:
- Conceptual / Logical / Physical Data Model;
- ERD;
- normalization;
- OLTP / OLAP;
- ACID / BASE;
- CAP;
- Polyglot Persistence;
- Source of Truth;
- Derived Store;
- Storage Selection Matrix.

### обязательные типы СУБД:
- relational;
- key-value;
- document;
- wide-column;
- graph;
- time-series;
- search engine;
- vector DB;
- object storage;
- data warehouse / lakehouse;
- event streaming platform.

### практика:
студенты заполняют Storage Selection Matrix для маркетплейса.

### acceptance criteria:
- студент понимает отличие OLTP от OLAP;
- студент может выбрать класс СУБД под задачу;
- студент понимает, что одна БД не должна решать все задачи;
- студент умеет определять source of truth и derived stores.
