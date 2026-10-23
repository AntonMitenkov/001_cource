# Бэклог задач (Backlog)

> Источник истины по темам и последовательности лекций: `specs/syllabus.md`.
> Все спеки `specs/lessons/*.spec.md` синхронизированы с syllabus (коммит «specs: sync lesson specs with syllabus»).
> Конвенция: этап `case` считается закрытым, если кейс встроен в draft/final (сноска «встроен»).

## Правила выполнения задач:
- одна лекция за итерацию;
- не начинать draft без spec;
- не делать final без review;
- все изменения фиксировать в git.

## Лекции:

### 1. Введение в System Design и проектирование ИТ-решений
**Статус:** ✅ Полный цикл до slides; открыт fact-check + тематическая правка (LRU/FIFO → кэширование на Лекцию 8)

- [x] spec — `specs/lessons/lesson-01.spec.md` (синхр. с syllabus)
- [x] brief — `content/lectures/01-intro-system-design/brief.md`
- [x] outline — `content/lectures/01-intro-system-design/outline.md`
- [x] draft — `content/lectures/01-intro-system-design/draft.md`
- [ ] case — (встроен в draft/final)
- [x] practice — `content/lectures/01-intro-system-design/practice.md`
- [x] diagrams — `content/lectures/01-intro-system-design/diagrams.md`
- [x] review — `content/lectures/01-intro-system-design/review.md`
- [ ] fact-check — реестр claim/source/confidence/status создан (коммит ee0a75c); закрытие — только человеком
- [x] final — `content/lectures/01-intro-system-design/final.md`
- [x] slides — `content/lectures/01-intro-system-design/slides.md`
- [x] ⚠️ правка: убрать фрагменты про LRU/FIFO-кэширование (тема Лекции 8 по syllabus) — выполнено; повторная проверка 14.10.2026: регистронезависимый grep по всей папке `01-intro-system-design/` — 0 вхождений

### 2. Предметная область, анализ процессов (Event Storming), требования и диаграмма Исикавы
**Статус:** 🟢 Полный цикл до slides. Теоретические блоки Исикава/6M, «5 почему», BABOK, SMART/MoSCoW добавлены (коммит ebc76c9); мостик к Л3 приведён в соответствие с syllabus и добавлены вопросы самопроверки по Блуму (коммит 3994d9e); practice расширен заданием ES+Исикава+5why+MoSCoW с рубрикой (коммит 7091a30); fact-check-реестр создан (ee0a75c). Остаток: расширение объёма final.md до нормы 85k (Этап E), человеческий review/fact-check.

- [x] spec — `specs/lessons/lesson-02.spec.md` (синхр. с syllabus)
- [x] brief — `content/lectures/02-domain-and-requirements/brief.md`
- [x] outline — `content/lectures/02-domain-and-requirements/outline.md`
- [x] draft — `content/lectures/02-domain-and-requirements/draft.md`
- [ ] case — (встроен в draft/final)
- [x] practice — `content/lectures/02-domain-and-requirements/practice.md`
- [x] diagrams — `content/lectures/02-domain-and-requirements/diagrams.md`
- [x] review — `content/lectures/02-domain-and-requirements/review.md`
- [ ] fact-check — реестр claim/source/confidence/status создан (коммит ee0a75c); закрытие — только человеком
- [x] final — `content/lectures/02-domain-and-requirements/final.md`
- [x] slides — `content/lectures/02-domain-and-requirements/slides.md`
- [x] ⚠️ доп. итерация: блоки «Диаграмма Исикавы (6M)», «5 почему», «Виды требований (BABOK)», «SMART + MoSCoW» добавлены в final.md (ebc76c9) и practice.md (7091a30); синхронизация slides.md — остаточная задача
- [ ] Расширение объёма final.md до ≥85 000 знаков (Этап E)

### 3. Концептуальная и логическая модели данных. Нормализация и эволюция схемы
**Статус:** 🟢 ФИНАЛ (20.10.2026): человеческий review закрыт вердиктом «Готов к итоговой генерации» (review.md, блок «Вердикт (Преподаватель)»), fact-check заполнен человеком (замечания №1–2 применены к тексту final/slides/practice), final.md переведён из кандидатов в финальную версию. Открытые хвосты: регламент академической честности (fact-check п.8, не блокирует), расширение объёма до нормы 85k (Этап E — поверх принятого текста). Старый невалидный контент («Архитектурные стили») удалён из репозитория (см. историю: `archive/lectures/legacy-03-architecture-styles`)

- [x] spec — `specs/lessons/lesson-03.spec.md` (синхр. с syllabus; frontmatter `status:` не менялся — только по команде пользователя)
- [x] brief — `content/lectures/03-data-modeling-normalization/brief.md`
- [x] outline — `content/lectures/03-data-modeling-normalization/outline.md`
- [x] draft — `content/lectures/03-data-modeling-normalization/draft.md`
- [ ] case — (отдельный файл не создавался, кейс встроен в draft/final)
- [x] practice — `content/lectures/03-data-modeling-normalization/practice.md`
- [x] diagrams — `content/lectures/03-data-modeling-normalization/diagrams.md`
- [x] review — `content/lectures/03-data-modeling-normalization/review.md` (AI-самопроверка + **человеческий вердикт «Готов к итоговой генерации», 20.10.2026**)
- [x] fact-check — `content/lectures/03-data-modeling-normalization/fact-check.md` (заполнен человеком 20.10.2026; замечания №1–2 применены; остаточный риск п.8 — регламент кафедры)
- [x] final — `content/lectures/03-data-modeling-normalization/final.md` (**финальная версия**, статус-шапка обновлена 20.10.2026)
- [x] slides — `content/lectures/03-data-modeling-normalization/slides.md` (пометки [фактчек] сняты по итогам human fact-check)
- [ ] Расширение объёма final.md до ≥85 000 знаков (Этап E; выполняется поверх принятого финального текста, без изменения статуса)

### 4. История, эволюция и виды СУБД. Транзакции, PACELC и Data Governance
**Статус:** 🟢 Полный пакет сгенерирован (11.10.2026, `content/lectures/04-data-architecture-dbms/`): brief → outline → draft → case/practice/diagrams → review (AI-самопроверка) → final-кандидат → slides. Ожидается **человеческое** решение вердикта в `review.md` и заполнение `fact-check.md`; до них final/slides — кандидаты. Spec не менялась (status: draft)

- [x] spec — `specs/lessons/lesson-04.spec.md`
- [x] brief — `content/lectures/04-data-architecture-dbms/brief.md`
- [x] outline — `content/lectures/04-data-architecture-dbms/outline.md`
- [x] draft — `content/lectures/04-data-architecture-dbms/draft.md` (с AI-самопроверкой в generation-report.md; человеческое ревью не проводилось)
- [x] case — `content/lectures/04-data-architecture-dbms/case.md` (развёрнутая версия; лекционная часть также встроена в draft, Case Study 20 мин)
- [x] practice — `content/lectures/04-data-architecture-dbms/practice.md`
- [x] diagrams — `content/lectures/04-data-architecture-dbms/diagrams.md` (8 диаграмм по перечню outline)
- [x] review — `content/lectures/04-data-architecture-dbms/review.md` (**AI-самопроверка по чек-листу; человеческий вердикт в блоке 9 не выставлен** — файл не заменяет ручное ревью)
- [ ] fact-check — протокол из 16 пунктов + реестр pending-human P-1…P-8 после снятия заглушек (коммит 9d8f98c); закрытие — только человеком
- [x] final — `content/lectures/04-data-architecture-dbms/final.md` (кандидат в финал до прохождения review/fact-check человеком; как в Лекции 3)
- [x] slides — `content/lectures/04-data-architecture-dbms/slides.md` (25 слайдов; кандидат до ручного review)

### 5. Взаимодействие приложений с СУБД, уязвимости и инструменты разработчика
**Статус:** 🟢 Полный пакет сгенерирован (12.10.2026): brief→outline→draft→case→practice→diagrams→review(AI)→final(кандидат)→slides(кандидат); ждут человеческого вердикта review и заполнения fact-check. Папка: `content/lectures/05-app-db-interaction-security-tools/`. Замечание: Л5 была создана позже Л6 (инверсия порядка), учтено в generation-report Л5.

- [x] spec — `specs/lessons/lesson-05.spec.md`
- [x] brief — `content/lectures/05-app-db-interaction-security-tools/brief.md`
- [x] outline — `content/lectures/05-app-db-interaction-security-tools/outline.md`
- [x] draft — `content/lectures/05-app-db-interaction-security-tools/draft.md`
- [x] case — `content/lectures/05-app-db-interaction-security-tools/case.md`
- [x] practice — `content/lectures/05-app-db-interaction-security-tools/practice.md`
- [x] diagrams — `content/lectures/05-app-db-interaction-security-tools/diagrams.md` (Д1–Д8)
- [x] review — `content/lectures/05-app-db-interaction-security-tools/review.md` (AI-самопроверка, вердикт человека не выставлен — НЕ замена ревью)
- [ ] fact-check — протокол создан + реестр pending-human P-1…P-6 после снятия заглушек (коммит bd6fd24); заполнение человеком — не выполнено
- [x] final — `content/lectures/05-app-db-interaction-security-tools/final.md` (кандидат в финал до прохождения review/fact-check человеком; как в Лекции 4)
- [x] slides — `content/lectures/05-app-db-interaction-security-tools/slides.md` (кандидат до ручного review)

### 6. Надежность данных: репликация, резервное копирование и восстановление
**Статус:** 🟢 Полный пакет сгенерирован (12.10.2026): brief→outline→draft→case→practice→diagrams→review(AI)→final(кандидат)→slides(кандидат); ждут человеческого вердикта review и заполнения fact-check. Папка: `content/lectures/06-data-reliability-recovery/`

- [x] spec — `specs/lessons/lesson-06.spec.md`
- [x] brief — `content/lectures/06-data-reliability-recovery/brief.md`
- [x] outline — `content/lectures/06-data-reliability-recovery/outline.md`
- [x] draft — `content/lectures/06-data-reliability-recovery/draft.md`
- [x] case — `content/lectures/06-data-reliability-recovery/case.md`
- [x] practice — `content/lectures/06-data-reliability-recovery/practice.md`
- [x] diagrams — `content/lectures/06-data-reliability-recovery/diagrams.md` (Д1–Д8)
- [x] review — `content/lectures/06-data-reliability-recovery/review.md` (AI-самопроверка, вердикт человека не выставлен — НЕ замена ревью)
- [ ] fact-check — `content/lectures/06-data-reliability-recovery/fact-check.md` (протокол создан, заполнение человеком — не выполнено)
- [x] final — `content/lectures/06-data-reliability-recovery/final.md` (кандидат в финал до прохождения review/fact-check человеком; как в Лекции 4)
- [x] slides — `content/lectures/06-data-reliability-recovery/slides.md` (25 слайдов, кандидат до ручного review)

### 7. System Design: финальная сборка, Peer-Review и защита отчета
**Статус:** 🟢 Полный пакет сгенерирован (12.10.2026): brief→outline→draft→case/practice/diagrams→review(AI)→final(кандидат)→slides; fact-check — протокол, ждёт человека; вердикт review — за человеком. Папка: `content/lectures/07-system-design-final-assembly-peer-review/`

- [x] spec — `specs/lessons/lesson-07.spec.md`
- [x] brief — `content/lectures/07-system-design-final-assembly-peer-review/brief.md`
- [x] outline — `content/lectures/07-system-design-final-assembly-peer-review/outline.md`
- [x] draft — `content/lectures/07-system-design-final-assembly-peer-review/draft.md`
- [x] case — `content/lectures/07-system-design-final-assembly-peer-review/case.md`
- [x] practice — `content/lectures/07-system-design-final-assembly-peer-review/practice.md`
- [x] diagrams — `content/lectures/07-system-design-final-assembly-peer-review/diagrams.md` (Д1–Д8)
- [x] review — `review.md` (AI-самопроверка; вердикт человека в §9 не выставлен — это НЕ замена ручному ревью)
- [ ] fact-check — `fact-check.md` создан как протокол (17 пунктов, 6 ⚠️); заполнение человеком не выполнено
- [x] final — `final.md` (КАНДИДАТ: до вердикта человека и закрытия fact-check)
- [x] slides — `slides.md` (25 слайдов, кандидат до ручного review)

### 8. Масштабирование: производительность, кэширование и аналитика (OLTP vs OLAP)
**Статус:** 🟢 Полный пакет сгенерирован; Л8 переписана как самодостаточный кандидат (коммит ebc76c9): структура 18 H2, без ссылок на draft. Ждут человеческого вердикта review и заполнения fact-check. Папка: `content/lectures/08-scaling-caching-oltp-olap/`

- [x] spec — `specs/lessons/lesson-08.spec.md`
- [x] brief — `content/lectures/08-scaling-caching-oltp-olap/brief.md`
- [x] outline — `content/lectures/08-scaling-caching-oltp-olap/outline.md`
- [x] draft — `content/lectures/08-scaling-caching-oltp-olap/draft.md`
- [x] case — `content/lectures/08-scaling-caching-oltp-olap/case.md`
- [x] practice — `content/lectures/08-scaling-caching-oltp-olap/practice.md`
- [x] diagrams — `content/lectures/08-scaling-caching-oltp-olap/diagrams.md`
- [x] review — `content/lectures/08-scaling-caching-oltp-olap/review.md` (AI-самопроверка, вердикт человека не выставлен)
- [ ] fact-check — `content/lectures/08-scaling-caching-oltp-olap/fact-check.md` (заполнение человеком — не выполнено)
- [x] final — `content/lectures/08-scaling-caching-oltp-olap/final.md` (кандидат; объём ≈46.5k — ниже нормы 85k, расширение в Этапе E)
- [x] slides — `content/lectures/08-scaling-caching-oltp-olap/slides.md` (кандидат до ручного review)


## Задачи коррекции (план AUDIT_MAP / этапный план, октябрь 2026)

### Закрыто
- [x] A1/A2/A3: снятие всех заглушек `[требуется проверка]` в final.md Л4–Л7 (коммиты 9d8f98c, bd6fd24, c67d1bb); тотальный grep = пусто
- [x] CJK-артефакты удалены, повторный скан чистый (коммит 73da3a5)
- [x] B1: мостик Л2→Л3 по syllabus (3994d9e)
- [x] B2: practice Л2 — задание Исикава/5why/ES/MoSCoW + рубрика (7091a30)
- [x] C1: переименование шаблона lesson-task.md. → lesson-task.md (7c2d38c)
- [x] C2: templates/peer-review.md, templates/architecture-brief.md + ссылки из README/practice Л1/Л7 (078a5fb, 73244c8)
- [x] C3: README синхронизирован с реальным состоянием (c6cd92d)
- [x] C4: единые статусные шапки-кандидаты во всех 8 final.md (471829e)
- [x] D1: fact-check-реестры Л1, Л2 созданы; pending-human в Л4–Л7 зарегистрированы (ee0a75c)

### Открыто (Этап E — расширение объёма до ≥85 000 знаков; порядок Л8→Л2→Л4→Л5→Л6→Л3→Л7→Л1)
- [ ] E-Л8: теория +кейсы +real-team +FAQ +самопроверка +связка с «Базы данных» +пересчёт тайминга (дефицит ≈38.5k)
- [ ] E-Л2: расширение блоков (дефицит ≈33k)
- [ ] E-Л4: расширение (дефицит ≈50.7k)
- [ ] E-Л5: расширение (дефицит ≈63.9k)
- [ ] E-Л6: расширение (дефицит ≈63.7k)
- [ ] E-Л3: расширение + отдельные секции 1.8 (управленческие решения) и 1.9 (визуальные материалы) по аудиту (дефицит ≈65k)
- [ ] E-Л7: расширение + секция 1.9 (дефицит ≈67k)
- [ ] E-Л1: расширение + fact-check человеком (дефицит ≈67.4k)

### Открыто (Этап F)
- [ ] F1: GLOSSARY-CONFLICTS.md — денормализация Л3↔Л8, OLAP/DWH, SLA/SLO, consistency, кэш vs connection pool
- [ ] F2: сквозная проверка ссылок knowledge//specs//content/ и «см. Лекцию N»
- [ ] F3: вычитка новых блоков (аббревиатуры, двойные прочтения, код ≤10 строк, обращение «вы»)

### Открыто (Этап G/H)
- [ ] G: VERIFICATION_REPORT.md (8 проверок)
- [ ] H: итоговый отчёт; остаточные риски для человека (review×8, fact-check×8, юридика 152-ФЗ/GDPR)
