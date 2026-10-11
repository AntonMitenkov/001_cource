---
id: lesson-04
title: "История, эволюция и виды СУБД. Транзакции, PACELC и Data Governance"
status: draft
duration: 80
domain: "маркетплейс / финтех / каршеринг / телемедицина"
depends_on:
  - lesson-03
next:
  - lesson-05
required_skills:
  - логическая модель данных (3НФ) из Лекции 3
---

Синхронизировано с `specs/syllabus.md` (источник истины).

Тема: «История, эволюция и виды СУБД. Транзакции, PACELC и Data Governance».

Краткая цель: сформировать понимание ландшафта современных СУБД, принципов транзакций (ACID) и подходов к защите и управлению данными (Data Governance).

### Обязательные концепции:
- эволюция СУБД: от иерархических до векторных и NoSQL;
- критерии выбора СУБД под конкретные задачи (Storage Selection Matrix);
- распределённые системы: теоремы CAP и PACELC;
- транзакции, свойства ACID, Commit/Rollback; уровни изоляции и проблемы конкурентного доступа (Dirty Read, Lost Update, Deadlock);
- OLTP vs OLAP; BASE; Polyglot Persistence; Source of Truth / Derived Store;
- целостность данных и Data Governance: PII, GDPR, 152-ФЗ, крипто-шреддинг.

### Типы СУБД (обзор через trade-offs, примеры а не стандарты):
relational, key-value, document, wide-column, graph, time-series, search engine, vector DB, object storage, data warehouse / lakehouse, event streaming platform.

### Практика:
заполнить Storage Selection Matrix для учебного кейса; обосновать выбор класса СУБД, анализ по PACELC и стратегию защиты PII.

### Acceptance criteria:
- студент различает классы СУБД и выбирает класс под задачу и паттерн доступа;
- студент объясняет ACID, уровни изоляции и аномалии конкурентного доступа;
- студент анализирует распределённую БД через CAP/PACELC;
- студент понимает, что одна БД не решает все задачи (source of truth vs derived stores);
- студент проектирует базовую стратегию Data Governance (PII, GDPR/152-ФЗ, crypto-shredding).

### Связь с лекциями:
- предыдущая: выбирает технологический стек для логических моделей, спроектированных в Лекции 3;
- следующая: переходит к практическим аспектам взаимодействия приложения с выбранной СУБД (Лекция 5).
