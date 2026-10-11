# Бэклог задач (Backlog)

## Для каждой лекции создай список задач:

> Шаблонный чек-лист ниже — это ПУСТОЙ образец, он не отражает реальное состояние уроков.
> Реальные статусы — только в секциях конкретных лекций. В шаблоне сняты ложные [x].

- [ ] spec
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

## Лекции:

### 1. Введение в System Design
**Статус:** ✅ Материалы созданы, готовы к ручной проверке

- [x] spec — `specs/lessons/lesson-01.spec.md`
- [x] brief — `content/lectures/01-intro-system-design/brief.md`
- [x] outline — `content/lectures/01-intro-system-design/outline.md`
- [x] draft — `content/lectures/01-intro-system-design/draft.md`
- [ ] case — (отдельный файл не создавался, кейс встроен в draft/final)
- [x] practice — `content/lectures/01-intro-system-design/practice.md`
- [x] diagrams — `content/lectures/01-intro-system-design/diagrams.md`
- [x] review — `content/lectures/01-intro-system-design/review.md` (самопроверка агента; финальное ревью человеком не выполнено)
- [ ] fact-check — требует проверки человеком
- [x] final — `content/lectures/01-intro-system-design/final.md`
- [x] slides — `content/lectures/01-intro-system-design/slides.md`

### 2. Предметная область и требования
**Статус:** ✅ Материалы созданы (brief/outline/draft/practice/diagrams/review/final/slides); review — самопроверка агента, fact-check не выполнен

- [x] spec — `specs/lessons/lesson-02.spec.md`
- [x] brief — `content/lectures/02-domain-and-requirements/brief.md`
- [x] outline — `content/lectures/02-domain-and-requirements/outline.md`
- [x] draft — `content/lectures/02-domain-and-requirements/draft.md`
- [ ] case — (отдельный файл не создавался, кейс встроен в draft/final)
- [x] practice — `content/lectures/02-domain-and-requirements/practice.md`
- [x] diagrams — `content/lectures/02-domain-and-requirements/diagrams.md`
- [x] review — `content/lectures/02-domain-and-requirements/review.md` (самопроверка агента; человек не проверял)
- [ ] fact-check — требует проверки человеком
- [x] final — `content/lectures/02-domain-and-requirements/final.md`
- [x] slides — `content/lectures/02-domain-and-requirements/slides.md`

### 3. Концептуальная и логическая модели данных. Нормализация и эволюция схемы
**Статус:** 🟡 Перегенерация 11.10.2026: brief / outline / draft / practice / diagrams / slides созданы; review.md — AI-самопроверка (не заменяет человека); fact-check.md — заготовка, не выполнен; final.md создан как КАНДИДАТ (final-draft) и по правилу «не делать final без review» ждёт ручного ревью; старый контент «Архитектурные стили» заархивирован в `archive/lectures/legacy-03-architecture-styles/`.

- [ ] spec — `specs/lessons/lesson-03.spec.md` существует, но это шаблон с плейсхолдерами (`title: "..."`, `domain: "маркетплейс / финтех / каршеринг / телемедицина"`, `required_skills: - ...`); статус `draft` НЕ менялся; заполнение title/domain — по команде пользователя
- [x] brief — `content/lectures/03-architecture-styles/brief.md` (перегенерирован)
- [x] outline — `content/lectures/03-architecture-styles/outline.md` (перегенерирован)
- [x] draft — `content/lectures/03-architecture-styles/draft.md` (перегенерирован)
- [ ] case — отдельный файл кейса не создавался (кейс встроен в draft/final; требуется решение, делать ли case.md)
- [x] practice — `content/lectures/03-architecture-styles/practice.md` (по practice-contract, 4 варианта контекстов, критерии оценки)
- [x] diagrams — `content/lectures/03-architecture-styles/diagrams.md` (8 диаграмм: Mermaid + ASCII)
- [ ] review — `review.md` создан как AI-самопроверка; финальное ревью требует проверки человеком — пункт остаётся открытым
- [ ] fact-check — `fact-check.md` создан как протокол со списком утверждений; заполняется только человеком — пункт открыт
- [ ] final — `final.md` создан как кандидат (помечен final-draft, ожидает review+fact-check человеком); отметка [x] будет поставлена только после принятия рецензентом
- [x] slides — `content/lectures/03-architecture-styles/slides.md` (23 слайда по slides-contract)

2. Предметная область и требования
3. Архитектурные стили
4. Архитектура данных и выбор СУБД
5. Интеграции, API и промежуточное хранение
6. Quality Attributes
7. Trade-offs, TCO, ATAM и ADR
8. Cloud Native, managed databases и финальная сборка

## Правила выполнения задач:
- одна лекция за итерацию;
- не начинать draft без spec;
- не делать final без review;
- все изменения фиксировать в git.
