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
- [ ] fact-check — требует проверки человеком
- [x] final — `content/lectures/01-intro-system-design/final.md`
- [x] slides — `content/lectures/01-intro-system-design/slides.md`
- [ ] ⚠️ правка: убрать фрагменты про LRU/FIFO-кэширование (тема Лекции 8 по syllabus)

### 2. Предметная область, анализ процессов (Event Storming), требования и диаграмма Исикавы
**Статус:** ✅ Полный цикл до slides; ⚠️ ТРЕБУЕТ ДОРАБОТКИ: в контенте отсутствуют обязательные темы syllabus (Исикава/6M, «5 почему», BABOK, MoSCoW)

- [x] spec — `specs/lessons/lesson-02.spec.md` (синхр. с syllabus)
- [x] brief — `content/lectures/02-domain-and-requirements/brief.md`
- [x] outline — `content/lectures/02-domain-and-requirements/outline.md`
- [x] draft — `content/lectures/02-domain-and-requirements/draft.md`
- [ ] case — (встроен в draft/final)
- [x] practice — `content/lectures/02-domain-and-requirements/practice.md`
- [x] diagrams — `content/lectures/02-domain-and-requirements/diagrams.md`
- [x] review — `content/lectures/02-domain-and-requirements/review.md`
- [ ] fact-check — требует проверки человеком
- [x] final — `content/lectures/02-domain-and-requirements/final.md`
- [x] slides — `content/lectures/02-domain-and-requirements/slides.md`
- [ ] ⚠️ доп. итерация: добавить в draft/final/slides блоки «Диаграмма Исикавы (6M)», «5 почему», «Виды требований (BABOK)», «SMART + MoSCoW» (см. knowledge/domain-analysis/ishikawa.md, requirements-babok.md)

### 3. Концептуальная и логическая модели данных. Нормализация и эволюция схемы
**Статус:** ✅ Перегенерирована по теме syllabus (PR #6). Полный цикл до final/slides; review — самопроверка агента, fact-check требует ручной проверки. Старый невалидный контент («Архитектурные стили») удалён из репозитория (см. историю: `archive/lectures/legacy-03-architecture-styles`)

- [x] spec — `specs/lessons/lesson-03.spec.md` (синхр. с syllabus)
- [x] brief — `content/lectures/03-data-modeling-normalization/brief.md`
- [x] outline — `content/lectures/03-data-modeling-normalization/outline.md`
- [x] draft — `content/lectures/03-data-modeling-normalization/draft.md`
- [ ] case — (отдельный файл не создавался, кейс встроен в draft/final)
- [x] practice — `content/lectures/03-data-modeling-normalization/practice.md`
- [x] diagrams — `content/lectures/03-data-modeling-normalization/diagrams.md`
- [x] review — `content/lectures/03-data-modeling-normalization/review.md` (самопроверка агента; финальное ревью человеком не выполнено)
- [ ] fact-check — требует проверки человеком (`fact-check.md` — протокол вопросов)
- [x] final — `content/lectures/03-data-modeling-normalization/final.md` (кандидат в финал до прохождения review/fact-check человеком)
- [x] slides — `content/lectures/03-data-modeling-normalization/slides.md`

### 4. История, эволюция и виды СУБД. Транзакции, PACELC и Data Governance
**Статус:** ⏳ Spec готова (синхр. с syllabus), контент не создавался

- [x] spec — `specs/lessons/lesson-04.spec.md`
- [ ] brief
- [ ] outline
- [ ] draft
- [ ] case
- [ ] practice
- [ ] diagrams
- [ ] review
- [ ] fact-check
- [ ] final
- [ ] slides

### 5. Взаимодействие приложений с СУБД, уязвимости и инструменты разработчика
**Статус:** ⏳ Spec переписана под тему syllabus (старая тема «Интеграции/API/очереди» заменена), контент не создавался

- [x] spec — `specs/lessons/lesson-05.spec.md`
- [ ] brief
- [ ] outline
- [ ] draft
- [ ] case
- [ ] practice
- [ ] diagrams
- [ ] review
- [ ] fact-check
- [ ] final
- [ ] slides

### 6. Надежность данных: репликация, резервное копирование и восстановление
**Статус:** ⏳ Spec готова (синхр. с syllabus), контент не создавался

- [x] spec — `specs/lessons/lesson-06.spec.md`
- [ ] brief
- [ ] outline
- [ ] draft
- [ ] case
- [ ] practice
- [ ] diagrams
- [ ] review
- [ ] fact-check
- [ ] final
- [ ] slides

### 7. System Design: финальная сборка, Peer-Review и защита отчета
**Статус:** ⏳ Spec готова (синхр. с syllabus), контент не создавался

- [x] spec — `specs/lessons/lesson-07.spec.md`
- [ ] brief
- [ ] outline
- [ ] draft
- [ ] case
- [ ] practice
- [ ] diagrams
- [ ] review
- [ ] fact-check
- [ ] final
- [ ] slides

### 8. Масштабирование: производительность, кэширование и аналитика (OLTP vs OLAP)
**Статус:** ⏳ Spec готова (синхр. с syllabus), контент не создавался

- [x] spec — `specs/lessons/lesson-08.spec.md`
- [ ] brief
- [ ] outline
- [ ] draft
- [ ] case
- [ ] practice
- [ ] diagrams
- [ ] review
- [ ] fact-check
- [ ] final
- [ ] slides
