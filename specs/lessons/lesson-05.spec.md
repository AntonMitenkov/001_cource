---
id: lesson-05
title: "Интеграции, API и промежуточное хранение: очереди, брокеры, события."
status: draft
duration: 80
domain: "маркетплейс / финтех / каршеринг / телемедицина"
depends_on:
  - lesson-04
next:
  - lesson-06
required_skills:
  - ...
---

Тема: "Интеграции, API и промежуточное хранение: очереди, брокеры, события".

### обязательные концепции:
- синхронные и асинхронные интеграции;
- queue vs broker vs event stream;
- task queue;
- message queue;
- pub/sub;
- event streaming;
- dead letter queue;
- retry queue;
- idempotency;
- at-least-once delivery;
- transactional outbox;
- inbox pattern;
- CDC;
- ordering;
- partition key;
- backpressure.

###  обязательные реализации:
- in-memory queue;
- task queue;
- message broker;
- pub/sub;
- event streaming;
- database as queue;
- transactional outbox;
- inbox pattern;
- DLQ;
- retry queue.

### практика:
спроектировать асинхронное оформление заказа в маркетплейсе.
### acceptance criteria:
- студент понимает отличие очереди от базы данных;
- студент может выбрать queue / broker / event stream;
- студент умеет проектировать retry и DLQ;
- студент понимает idempotency;
- студент может объяснить outbox и inbox.
