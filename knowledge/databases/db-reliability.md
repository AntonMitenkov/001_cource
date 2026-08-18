# Надёжность БД (Database Reliability)

# Надёжность баз данных: backup, replication, security

## Backup (Резервное копирование)

**Назначение:** Создание копий данных для восстановления после сбоев,
ошибок или катастроф.

### Типы бэкапов

**Full Backup (Полный бэкап):**
- Копия всей БД
- Самый объёмный, но самый простой для восстановления
- Пример: `pg_dump` для PostgreSQL, `mysqldump` для MySQL

**Incremental Backup (Инкрементальный бэкап):**
- Копия изменений с момента последнего бэкапа
- Меньше объём, быстрее создание
- Сложнее восстановление (нужен full + все incremental)

**Differential Backup (Дифференциальный бэкап):**
- Копия изменений с момента последнего full backup
- Больше incremental, но проще восстановление (full + последний
  differential)

**WAL/Transaction Log Backup:**
- Копия журнала транзакций (write-ahead log)
- Point-in-time recovery (восстановление на конкретный момент времени)
- Пример: PostgreSQL WAL archiving, MySQL binlog

### Стратегии бэкапов

**3-2-1 Rule (Правило 3-2-1):**
- **3** копии данных (1 production + 2 backup)
- **2** разных носителя (диск + лента, S3 + Glacier)
- **1** копия off-site (другой регион, другое облако)

**Backup Frequency (Частота):**
- **RPO-driven:** Какую потерю данных вы можете себе позволить?
- Пример: RPO = 1 час → бэкапы каждый час
- Пример: RPO = 1 день → ежедневные бэкапы

**Retention Policy (Политика хранения):**
- Сколько хранить бэкапы?
- Пример: daily backups 30 дней, weekly 1 год, monthly 7 лет (compliance)

**Testing (Тестирование восстановления):**
- **Критично:** Бэкап без теста восстановления бесполезен
- Регулярно восстанавливайте бэкапы в тестовую среду
- Документируйте procedure и время восстановления

### Примеры инструментов

**PostgreSQL:**
- `pg_dump` (logical backup)
- `pg_basebackup` (physical backup)
- WAL archiving + WAL-E/WAL-G
- Barman, pgBackRest

**MySQL:**
- `mysqldump` (logical)
- MySQL Enterprise Backup (physical)
- Percona XtraBackup
- Binlog archiving

**MongoDB:**
- `mongodump` (logical)
- File system snapshots (physical)
- MongoDB Cloud Manager (managed backups)

**Managed Services:**
- AWS RDS: automated snapshots, point-in-time recovery
- Azure SQL: automated backups, geo-redundant storage
- Google Cloud SQL: automated backups, binary logs

---

## Replication (Репликация)

**Назначение:** Копирование данных на несколько узлов для повышения
доступности, производительности и отказоустойчивости.

### Типы репликации

**Synchronous Replication (Синхронная):**
- Транзакция подтверждается только после записи на все реплики
- **Гарантия:** Данные не потеряются при сбое primary
- **Цена:** Высокая latency (ожидание всех реплик)
- **Пример:** PostgreSQL synchronous streaming replication

**Asynchronous Replication (Асинхронная):**
- Транзакция подтверждается сразу, репликация происходит фоном
- **Гарантия:** Данные могут потеряться при сбое primary (до репликации)
- **Цена:** Возможна потеря данных (replication lag)
- **Пример:** MySQL async replication, MongoDB replica sets (default)

**Semi-synchronous Replication (Полусинхронная):**
- Транзакция подтверждается после записи на majority реплик
- **Компромисс:** Баланс между latency и durability
- **Пример:** MySQL semi-sync, Cassandra QUORUM consistency

### Топологии репликации

**Primary-Replica (Master-Slave):**

Primary (read/write) → Replica 1 (read-only)
→ Replica 2 (read-only)
→ Replica 3 (read-only)

- Один primary принимает записи
- Реплики для чтения и failover
- **Пример:** PostgreSQL streaming replication, MySQL replication

**Multi-Primary (Master-Master):**
Node 1 (read/write) ↔ Node 2 (read/write)

- Несколько узлов принимают записи
- Сложнее conflict resolution
- **Пример:** Galera Cluster (MySQL), CockroachDB

**Cascading Replication:**
Primary → Replica 1 → Replica 2 → Replica 3
- Реплика реплицирует на другие реплики
- Снижает нагрузку на primary
- **Пример:** PostgreSQL cascading replication

### Read Replicas (Реплики для чтения)

**Назначение:** Разгрузка primary от read-запросов.

**Преимущества:**
- Масштабирование чтения (scale-out reads)
- Изоляция аналитических запросов от транзакционных
- Географическая близость к пользователям (read replica в другом регионе)

**Ограничения:**
- Replication lag: read replica может отставать от primary
- Не подходит для read-your-writes consistency
- Сложность маршрутизации запросов (какие на primary, какие на replica)

**Примеры использования:**
- Отчёты и аналитика на read replica
- Полнотекстовый поиск (репликация в Elasticsearch)
- Backup с read replica (не влияет на primary)

---

## Failover (Переключение при сбое)

**Назначение:** Автоматическое переключение на резервный узел при сбое
primary.

### Типы failover

**Automatic Failover:**
- Система сама обнаруживает сбой и переключается
- **Требования:** Health checks, consensus algorithm
- **Пример:** PostgreSQL Patroni, MongoDB replica sets, AWS RDS Multi-AZ

**Manual Failover:**
- Оператор вручную инициирует переключение
- **Преимущество:** Контроль, нет ложных срабатываний
- **Недостаток:** Время реакции зависит от человека

**Semi-automatic Failover:**
- Система обнаруживает сбой, но требует подтверждения оператора
- **Компромисс:** Быстрое обнаружение + человеческий контроль

### Компоненты failover

**Health Checks:**
- Периодические проверки доступности primary
- **Метрики:** TCP connection, query response time, replication lag
- **Пример:** pg_isready, custom health check scripts

**Consensus Algorithm:**
- Определение, действительно ли primary упал (избегаем split-brain)
- **Алгоритмы:** Raft, Paxos
- **Пример:** etcd, Consul, ZooKeeper для leader election

**Promotion:**
- Переключение read replica в primary
- **Шаги:**
  1. Остановить репликацию на новой primary
  2. Обновить DNS/connection strings
  3. Перенаправить трафик

**Split-Brain Prevention:**
- Ситуация, когда два узла считают себя primary
- **Решения:**
  - Quorum (majority vote)
  - Fencing (STON
