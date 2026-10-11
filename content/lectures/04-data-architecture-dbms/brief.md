# Бриф Лекции 4

## Тема
История, эволюция и виды СУБД. Транзакции, PACELC и Data Governance

## Соответствие источнику истины
Тема, цель, ключевые темы и практический результат взяты из `specs/syllabus.md` (Лекция 4) и `specs/lessons/lesson-04.spec.md` (frontmatter `status: draft`, `depends_on: lesson-03`). Папка контента: `content/lectures/04-data-architecture-dbms/` — slug задан пользователем в команде текущей итерации; артефакт урока по `specs/module-map.md` (Лекция 4): «Матрица выбора СУБД + Стратегия Data Governance».

## Цель лекции
Научить студентов выбирать класс СУБД под конкретную задачу: понимать эволюцию систем хранения данных (от иерархических до векторных и NoSQL), различать типы СУБД через их сильные стороны и ограничения, анализировать распределённые базы через теоремы CAP и PACELC, объяснять свойства транзакций ACID, уровни изоляции и аномалии конкурентного доступа, проектировать базовую стратегию Data Governance (защита PII, GDPR/152-ФЗ, crypto-shredding) и осознанно строить полиглотное хранение с разделением Source of Truth и Derived Store.

## Ключевые сообщения
1. **У каждой волны СУБД своя причина.** Эволюция «файлы → иерархические → сетевые → реляционные → коммерческие/открытые RDBMS → облачные → NoSQL → векторные» — это реакция на новые задачи (связи M:N, целостность, масштаб, гибкая схема, геораспределённость, AI/семантика). История учит: технология выбирается под проблему, а не «потому что модная».
2. **Нет универсальной СУБД.** Каждый класс (relational, key-value, document, wide-column, graph, time-series, search engine, vector DB, object storage, data warehouse/lakehouse, event streaming) оптимизирован под свой паттерн доступа. Выбор — это Storage Selection Matrix: тип нагрузки, объём, read/write ratio, consistency, latency, retention, cost, compliance, экспертиза команды.
3. **CAP — про отказ сети, PACELC — про каждый день.** При сетевом разбиении (P) выбираем A или C; в штатном режиме (E) платим латентностью (L) за согласованность (C). Формула PACELC даёт язык для разговора с вендором и для ADR.
4. **ACID — это контракт приложения с данными.** Атомарность (Commit/Rollback), Consistency (ограничения из Лекции 3 работают), Изоляция (уровни SQL: Read Uncommitted → Serializable и аномалии: Dirty Read, Non-repeatable Read, Phantom Read, Lost Update, Deadlock), Durability (WAL). Чем выше изоляция — тем ниже конкурентность: это trade-off, а не настройка «по умолчанию навсегда».
5. **BASE и eventual consistency — не «плохой ACID», а другая точка компромисса** для распределённых write-heavy систем; приложение должно уметь жить с устаревшим чтением (read-your-writes, causal consistency — промежуточные модели).
6. **Polyglot Persistence: одна система — много хранилищ, но один источник истины на факт.** Derived store (поисковый индекс, кэш, аналитическая копия) — всегда проекция Source of Truth, а не параллельная правда. OLTP и OLAP — разные миры: нормализованные строки против денормализованных колонок.
7. **Data Governance — архитектурное требование, а не юридическая формальность.** PII требует классификации, локализации (152-ФЗ), права на удаление (GDPR); паттерны защиты — маскирование, токенизация, шифрование at rest/in transit; crypto-shredding решает задачу «удалить данные из бэкапов и реплик» через удаление ключа в KMS. Выбор СУБД должен учитывать эти ограничения заранее.
8. **Итоговый артефакт лекции** — заполненная Storage Selection Matrix и ADR выбора класса СУБД для сквозного кейса «Каршеринг»; они входят в Architecture Blueprint и становятся ТЗ для курса «Базы данных».

## Целевая аудитория
- Студенты направления «Бизнес-информатика» и «Программная инженерия»
- ИТ-менеджеры и Product Owners
- Начинающие Solution Architects и системные аналитики
- Слушатели, готовящиеся к курсу «Базы данных» (SQL и администрирование СУБД не требуются на входе)

## Сквозной кейс курса
**Сервис каршеринга** (развивается с Лекций 1–2; параметры унаследованы: ~200 автомобилей, 3 города, MVP за 3 месяца, команда 8 человек — см. Лекции 2–3). На Лекции 3 спроектированы концептуальная и логическая модели в 3НФ по контекстам Бронирование / Телематика / Оплата / Штрафы / Поддержка. На Лекции 4 каждый контекст получает «дом»: транзакционные ядра (Бронирование, Оплата) — под ACID/OLTP-нагрузку; телеметрия GPS (порядка события каждые ~10 секунд на автомобиль — оценка из Лекции 3, [требуется проверка]) — под write-heavy/time-series профиль; поиск свободных машин рядом — под гео/поисковый профиль. Итог — полиглотный стек с явно обозначенным Source of Truth и derived-копиями, плюс стратегия защиты PII клиентов (ФИО, телефон, документы, треки поездок) по GDPR/152-ФЗ.

## Кейс для Hook
«Команда выбрала документную БД, потому что „NoSQL масштабируется лучше“»: стартап перевёл финансовые транзакции и бронирования в СУБД без полных ACID-гарантий; при пиковой нагрузке два клиента забронировали один автомобиль одновременно (lost update), а отчёт о выручке разошёлся с выпиской платежей. Второй эпизод той же истории: в одну базу положили и транзакции, и телеметрию, и аналитику — каждый аналитический запрос сканировал миллионы строк поверх OLTP-блокировок и деградировал пользовательский опыт. Вопросы аудитории: можно ли было предсказать провал на этапе выбора? Какими критериями? Что говорит PACELC о поведении системы при обрыве канала между дата-центрами? Можно ли было спасти ситуацию, не меняя СУБД, а изменив уровень изоляции?

## Обязательное покрытие ключевых тем (по specs/syllabus.md и lesson-04.spec.md)
1. Эволюция СУБД: от иерархических до векторных и NoSQL
2. Критерии выбора СУБД под конкретные задачи (Storage Selection Matrix)
3. Распределённые системы: теоремы CAP и PACELC
4. Транзакции, свойства ACID, Commit/Rollback
5. Уровни изоляции и проблемы конкурентного доступа (Dirty Read, Lost Update, Deadlock)
6. OLTP vs OLAP; BASE; Polyglot Persistence; Source of Truth / Derived Store
7. Целостность данных и Data Governance: PII, GDPR, 152-ФЗ, крипто-шреддинг
8. Обзор типов СУБД через trade-offs: relational, key-value, document, wide-column, graph, time-series, search engine, vector DB, object storage, data warehouse/lakehouse, event streaming platform

## Практический результат урока
Заполненная Storage Selection Matrix для контекстов кейса «Каршеринг» (тип нагрузки, объём, read/write ratio, latency, consistency, retention, compliance, стоимость, экспертиза); обоснованный выбор класса СУБД с анализом по PACELC; фрагмент стратегии Data Governance (классификация PII, меры защиты, подход к удалению — crypto-shredding); черновик ADR выбора стека хранения. Результат входит в итоговый Architecture Blueprint.

## Основные термины (согласованы с knowledge/glossary.md)
- ACID; Транзакция; COMMIT / ROLLBACK; WAL
- Уровни изоляции: Read Uncommitted / Read Committed / Repeatable Read / Serializable
- Dirty Read; Non-repeatable Read; Phantom Read; Lost Update; Deadlock; MVCC
- CAP-теорема; PACELC; CP/AP-системы; Strong / Eventual / Causal consistency; Read-your-writes
- BASE (Basic Availability, Soft State, Eventual Consistency)
- OLTP; OLAP; ETL/ELT
- Polyglot Persistence; Source of Truth; Derived Store
- Data Governance; PII; GDPR; 152-ФЗ; Маскирование; Токенизация; Шифрование at rest / in transit; Crypto-shredding; KMS
- Классы СУБД: реляционные, key-value, документные, wide-column, графовые, time-series, поисковые движки, векторные, объектные хранилища, DWH/lakehouse, event streaming
- TCO; NFR; ADR; Resume-Driven Development (все — из глоссария курса)

## Визуальные материалы
1. Таймлайн эволюции СУБД (таблица «период → модель → проблема, которую решила»)
2. Сводная таблица классов СУБД (модель данных / транзакции / масштабирование / типовые задачи / «когда не использовать»)
3. Схема CAP-треугольника и таблица PACELC-классификации систем
4. Таблица «уровни изоляции × аномалии»
5. Mermaid-схема полиглотного стека каршеринга: Source of Truth → CDC/ETL → Derived Stores
6. Пустой шаблон Storage Selection Matrix (для практики) и схема crypto-shredding (персональный ключ в KMS → удаление ключа)

## Риски и анти-паттерны
- ❌ Resume-Driven Development: выбор «модной» технологии вместо критериев задачи
- ❌ «Одна СУБД для всего»: OLTP-движок под аналитику и наоборот
- ❌ Очередь/streaming-лог как основное хранилище бизнес-состояния (нарушение контракта: очереди — передача событий, не замена БД)
- ❌ Смешение Source of Truth и derived store: «правда» начинает жить в двух местах
- ❌ Eventual consistency там, где нужен strong (бронирование одного автомобиля двумя клиентами, списание баланса)
- ❌ Хранение PII в открытом виде «где попало» + естественные ключи-идентификаторы → невозможность выполнить право на удаление
- ❌ Игнорирование регуляторики (data residency по 152-ФЗ) при выборе managed-облака [детали локализации — проверять по актуальной редакции закона]

## Связь с другими лекциями
- **Лекция 3 (depends_on):** логическая модель в 3НФ — вход для матрицы выбора СУБД; ограничения (PK/FK/CHECK) — основа свойства Consistency в ACID.
- **Лекция 1:** NFR и SLO/SLA — источник требований к consistency/latency/availability; ADR — формат фиксации выбора стека.
- **Лекция 5 (next):** выбранная СУБД → взаимодействие приложения с ней: пулы соединений, ORM vs Raw SQL, SQL-инъекции.
- **Лекция 6:** репликация и RPO/RTO развивают тему CAP/PACELC и Durability.
- **Лекция 8:** OLTP vs OLAP углубляется в кэширование, индексы, ETL/ELT и аналитические хранилища.
- **Курс «Базы данных» (следующий семестр):** реализация выбранного стека (PostgreSQL, MongoDB, Redis, Qdrant — как учебные примеры парадигм, не стандарты).

## Источники (knowledge-база курса)
- knowledge/databases/dbms-history.md (эволюция; Codd 1970)
- knowledge/databases/dbms-types.md (11 классов СУБД; Kleppmann 2017, гл. 2)
- knowledge/databases/storage-selection.md (критерии, Storage Selection Matrix, red/green flags)
- knowledge/databases/cap-pacelc.md (Brewer 2000; Gilbert & Lynch 2002; Abadi 2010)
- knowledge/databases/acid-base.md (ACID/BASE, модели согласованности)
- knowledge/databases/transactions-acid.md (Gray & Reuter 1993; уровни изоляции, deadlock)
- knowledge/databases/oltp-olap.md (конфликты OLTP/OLAP, ETL/ELT)
- knowledge/databases/data-governance.md (PII, GDPR, 152-ФЗ, crypto-shredding; NIST SP 800-122)
- knowledge/glossary.md; knowledge/course-style.md; knowledge/no-hallucination.md
- content/lectures/03-data-modeling-normalization/draft.md (предыдущая лекция, сквозной кейс, мостик)
