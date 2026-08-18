# Выбор СУБД: критерии и матрица решений

## Ключевые критерии выбора

### 1. Read/Write Ratio (Соотношение чтения и записи)

**Read-heavy (90%+ чтение):**
- Кэширование (Redis, Memcached)
- OLAP-системы (ClickHouse, BigQuery)
- Поисковые движки (Elasticsearch)

**Write-heavy (90%+ запись):**
- Time-series (InfluxDB, TimescaleDB)
- Event streaming (Kafka, Pulsar)
- Wide-column (Cassandra)

**Balanced (50/50):**
- Реляционные БД (PostgreSQL, MySQL)
- Document (MongoDB)

**Вопросы для анализа:**
- Сколько операций чтения на одну запись?
- Какой паттерн доступа: point queries или range scans?
- Нужна ли агрегация на лету?

 

### 2. Latency (Задержка)

**< 1 мс (ультранизкая):**
- In-memory (Redis, Memcached)
- Key-value с SSD (Aerospike)

**1–10 мс (низкая):**
- Реляционные БД с индексами
- Document DB (MongoDB)

**10–100 мс (средняя):**
- Wide-column (Cassandra)
- Graph DB (Neo4j для глубоких обходов)

**100+ мс (высокая, приемлема для аналитики):**
- OLAP (ClickHouse, BigQuery)
- Data warehouse (Snowflake, Redshift)

**Вопросы для анализа:**
- Какой SLA на response time?
- Есть ли hard deadlines (real-time системы)?
- Какой percentile важен (p50, p95, p99)?

 

### 3. Volume (Объём данных)

**< 100 GB:**
- Любая СУБД подойдёт
- Выбор по другим критериям

**100 GB — 1 TB:**
- Реляционные БД с партиционированием
- Document DB
- Wide-column

**1 TB — 100 TB:**
- Wide-column (Cassandra, ScyllaDB)
- Distributed SQL (CockroachDB, TiDB)
- OLAP (ClickHouse)

**100 TB+:**
- Event streaming (Kafka)
- Data lake (S3 + Athena/Presto)
- Specialized (time-series, graph)

**Вопросы для анализа:**
- Какой текущий объём данных?
- Какой прогноз роста (2x в год, 10x в год)?
- Нужна ли архивация старых данных?

 

### 4. Consistency (Согласованность)

**Strong consistency (обязательно):**
- Финансовые транзакции
- Инвентаризация (нельзя продать больше, чем есть)
- Реляционные БД (PostgreSQL, MySQL InnoDB)
- Distributed SQL (CockroachDB, Spanner)

**Eventual consistency (приемлемо):**
- Социальные ленты
- Логирование
- Аналитика
- Wide-column (Cassandra), DynamoDB

**Causal consistency (компромисс):**
- Комментарии и ответы (причинно-следственные связи)
- MongoDB, Riak

**Вопросы для анализа:**
- Что будет, если пользователь увидит устаревшие данные?
- Есть ли бизнес-процессы, зависящие от строгой согласованности?
- Можно ли компенсировать несогласованность на уровне приложения?

 

### 5. Retention (Срок хранения)

**Краткосрочное (< 30 дней):**
- Кэширование (Redis с TTL)
- Session storage

**Среднесрочное (30 дней — 1 год):**
- Активные данные в OLTP
- Логи для отладки

**Долгосрочное (1+ лет):**
- Архивы (S3, Glacier)
- Data warehouse
- Compliance-данные

**Immutable (неизменяемые):**
- Event log (Kafka)
- Audit logs
- Blockchain-подобные системы

**Вопросы для анализа:**
- Какие регуляторные требования (GDPR, PCI DSS)?
- Нужен ли replay истории?
- Какая стоимость хранения на разных уровнях?

 

### 6. Cost (Стоимость)

**Компоненты стоимости:**
- **License:** Open-source vs commercial
- **Infrastructure:** CPU, RAM, storage, network
- **Operations:** DBA, мониторинг, бэкапы
- **Development:** Сложность разработки, ORM, миграции

**Экономичные решения:**
- PostgreSQL (open-source, мощный)
- MySQL (open-source, широко распространён)
- SQLite (embedded, нулевая стоимость)

**Коммерческие решения (оправданы при scale):**
- Oracle (enterprise features, support)
- Snowflake (auto-scaling, pay-per-query)
- Managed services (RDS, Atlas)

**Вопросы для анализа:**
- Какой бюджет на инфраструктуру?
- Есть ли in-house экспертиза?
- Какая стоимость простоя (downtime cost)?

 

### 7. Compliance (Соответствие регуляторным требованиям)

**PCI DSS (платёжные данные):**
- Шифрование at rest и in transit
- Audit logging
- Access control
- Tokenization

**GDPR (персональные данные ЕС):**
- Right to be forgotten (удаление данных)
- Data portability
- Consent management

**HIPAA (медицинские данные США):**
- Encryption
- Audit trails
- Business Associate Agreements (BAA)

**SOC 2 (аудит безопасности):**
- Access control
- Monitoring
- Incident response

**Вопросы для анализа:**
- Какие стандарты применимы к вашему домену?
- Нужна ли сертификация облачного провайдера?
- Где должны храниться данные (data residency)?

 

## Storage Selection Matrix

### Матрица принятия решений

```
Шаг 1: Определите тип нагрузки
├─ OLTP (транзакции) → Реляционные, Document, Key-Value
├─ OLAP (аналитика) → Data Warehouse, OLAP DB
├─ Real-time streaming → Event Streaming
└─ Specialized → Graph, Time-series, Search, Vector

Шаг 2: Оцените объём данных
├─ < 100 GB → Любая СУБД
├─ 100 GB — 1 TB → Реляционные + партиционирование, Document
├─ 1 TB — 100 TB → Wide-column, Distributed SQL, OLAP
└─ 100 TB+ → Event streaming, Data lake

Шаг 3: Определите требования к consistency
├─ Strong consistency → Реляционные, Distributed SQL
├─ Eventual consistency → Wide-column, Document, DynamoDB
└─ Causal consistency → MongoDB, Riak

Шаг 4: Оцените read/write ratio
├─ Read-heavy (>90%) → Кэш, OLAP, Search
├─ Write-heavy (>90%) → Time-series, Event streaming, Wide-column
└─ Balanced → Реляционные, Document

Шаг 5: Проверьте latency требования
├─ < 1 мс → In-memory (Redis)
├─ 1–10 мс → Реляционные, Document
├─ 10–100 мс → Wide-column, Graph
└─ 100+ мс → OLAP, Data warehouse

Шаг 6: Учтите compliance
├─ PCI DSS → Шифрование, audit, tokenization
├─ GDPR → Right to be forgotten, data portability
├─ HIPAA → Encryption, BAA
└─ SOC 2 → Access control, monitoring
```

 

### Примеры выбора

**Пример 1: E-commerce платформа**
- **Задача:** Каталог товаров, заказы, пользователи
- **Объём:** 500 GB
- **Нагрузка:** 80% чтение, 20% запись
- **Consistency:** Strong для заказов и платежей
- **Latency:** < 10 мс
- **Выбор:**
  - PostgreSQL (заказы, пользователи)
  - MongoDB (каталог товаров — гибкая схема)
  - Redis (кэш сессий, корзина)
  - Elasticsearch (поиск товаров)

 

**Пример 2: IoT платформа**
- **Задача:** Сбор телеметрии с 1 млн устройств
- **Объём:** 50 TB
- **Нагрузка:** 99% запись, 1% чтение
- **Consistency:** Eventual
- **Latency:** < 100 мс для записи
- **Retention:** 2 года
- **Выбор:**
  - TimescaleDB (time-series данные)
  - Kafka (event streaming, буферизация)
  - S3 (архив старых данных)
  - ClickHouse (аналитика)

 

**Пример 3: Социальная сеть**
- **Задача:** Ленты новостей, сообщения, граф друзей
- **Объём:** 10 TB
- **Нагрузка:** 70% чтение, 30% запись
- **Consistency:** Eventual (лента), Strong (сообщения)
- **Latency:** < 50 мс для ленты
- **Выбор:**
  - Cassandra (ленты новостей, сообщения)
  - Neo4j (граф друзей, рекомендации)
  - Redis (кэш популярных постов)
  - Elasticsearch (поиск постов)

 

**Пример 4: Финтех стартап**
- **Задача:** Платежи, балансы, транзакции
- **Объём:** 50 GB
- **Нагрузка:** 60% чтение, 40% запись
- **Consistency:** Strong (обязательно)
- **Compliance:** PCI DSS
- **Latency:** < 10 мс
- **Выбор:**
  - PostgreSQL (основная БД, ACID транзакции)
  - Redis (кэш балансов с инвалидацией)
  - Snowflake (аналитика, отчёты)
  - S3 (бэкапы, аудит-логи)

 

## Шаблон Storage Selection Matrix

Для каждого компонента системы заполните таблицу:

| Критерий | Требование | Приоритет | Выбранная СУБД | Обоснование |
|---|---|---|---|---|
| Тип нагрузки | OLTP / OLAP / Streaming | Высокий | | |
| Объём данных | Текущий / прогноз | Высокий | | |
| Read/Write ratio | % чтение / % запись | Средний | | |
| Latency (p95) | < N мс | Высокий | | |
| Consistency | Strong / Eventual / Causal | Высокий | | |
| Retention | N дней / месяцев / лет | Средний | | |
| Compliance | PCI / GDPR / HIPAA | Высокий | | |
| Cost | Бюджет $/мес | Средний | | |
| Экспертиза команды | Есть / нужно обучить | Средний | | |
| Масштабирование | Вертикальное / горизонтальное | Высокий | | |

 

## Чек-лист для выбора СУБД

### Перед выбором ответьте на вопросы:

**Функциональные требования:**
- [ ] Какой тип данных (структурированные, полуструктурированные,
  неструктурированные)?
- [ ] Какие операции преобладают (CRUD, агрегации, поиск, аналитика)?
- [ ] Нужны ли сложные запросы (JOIN, подзапросы, оконные функции)?
- [ ] Какая схема данных (стабильная, изменчивая, без схемы)?

**Нефункциональные требования:**
- [ ] Какой ожидаемый объём данных (сейчас, через год, через 3 года)?
- [ ] Какой SLA на latency (p50, p95, p99)?
- [ ] Какой SLA на availability (99.9%, 99.99%, 99.999%)?
- [ ] Какая consistency модель приемлема?

**Операционные требования:**
- [ ] Есть ли in-house экспертиза по СУБД?
- [ ] Какой бюджет на инфраструктуру и лицензирование?
- [ ] Нужна ли managed service или self-hosted?
- [ ] Какие compliance требования?

**Архитектурные требования:**
- [ ] Монолит или микросервисы?
- [ ] Нужна ли геораспределённость?
- [ ] Как будет происходить масштабирование (вертикальное,
  горизонтальное)?
- [ ] Как интегрируется с другими системами?

 

## Red Flags (когда выбор неправилен)

- [ ] Используете OLTP-БД для аналитики (медленные запросы)
- [ ] Используете NoSQL для финансовых транзакций (нет ACID)
- [ ] Храните файлы в реляционной БД (используйте object storage)
- [ ] Одна БД для всего (polyglot persistence лучше)
- [ ] Не учли стоимость операций (DBA, мониторинг, бэкапы)
- [ ] Выбрали СУБД только потому, что «модная» (нужны объективные
  критерии)
- [ ] Не протестировали на реальных объёмах данных
- [ ] Не учли рост нагрузки в перспективе 2–3 лет

 

## Green Flags (когда выбор правильный)

- [ ] СУБД соответствует типу нагрузки (OLTP/OLAP/streaming)
- [ ] Масштабируется предсказуемо (горизонтально или вертикально)
- [ ] Есть community и документация
- [ ] Команда имеет экспертизу или может её получить
- [ ] Стоимость владения приемлема (TCO)
- [ ] Соответствует compliance требованиям
- [ ] Интегрируется с существующей экосистемой
- [ ] Проведено нагрузочное тестирование на реальных данных
- [ ] Есть план миграции при смене требований
