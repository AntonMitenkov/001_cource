# Fact-check Лекции 2 — реестр проверяемых утверждений

> **Статус: НЕ ЗАВЕРШЁН.** По правилам курса fact-check завершает только человек.
> AI подготовил реестр ключевых утверждений final.md с источниками и уверенностью.
> Статус `confirmed-by-knowledge-base` означает наличие источника в `knowledge/**` — это НЕ вердикт человека.
> Итог: human verdict отсутствует — документ `final.md` остаётся кандидатом.

## Реестр (claim / source / confidence / status)

| № | Утверждение (claim) | Источник (source) | Confidence | Status |
|---|---|---|---|---|
| 1 | Bounded Context — граница семантической целостности модели предметной области; один термин — одно значение внутри контекста | knowledge/glossary.md:11, knowledge/domain-analysis/ddd-bounded-contexts.md | high | confirmed-by-knowledge-base |
| 2 | Event Storming — фасилитированная сессия с цветовой кодировкой карточек (доменные события — оранжевые, команды — синие, акторы — жёлтые и т.д.) | knowledge/domain-analysis/event-storming.md | high | confirmed-by-knowledge-base |
| 3 | Диаграмма Исикавы («рыбья кость»), классический набор категорий 6M; метод предложен Каору Исикавой (Япония, ок. 1968–1970-е) | knowledge/domain-analysis/ishikawa.md; историческая атрибуция — общедостатная, без цитаты первоисточника | medium | pending-human |
| 4 | «5 почему» — итеративный опрос для выхода на корневую причину; остановка критерием «причина вне зоны контроля/связана с процессом» | knowledge/domain-analysis/ishikawa.md (раздел про 5 why), общепринятая практика Toyota | medium | confirmed-by-knowledge-base |
| 5 | Классификация видов требований по BABOK (business/stakeholder/solution requirements и т.п.) | knowledge/domain-analysis/requirements-babok.md; внешняя привязка к IIBA BABOK Guide — сверить редакцию | medium | pending-human |
| 6 | SMART-критерии для FR (Specific, Measurable, Achievable, Relevant, Time-bound) | общепринятое определение; закреплено в knowledge/domain-analysis/requirements-babok.md | high | confirmed-by-knowledge-base |
| 7 | MoSCoW — приоритизация Must have / Should have / Could have / Won't have (this time) | общедостатный метод (Daine Cockburn, 1994); закреплён в practice.md Л2 | medium | pending-human |
| 8 | Quality Attribute Scenarios — формат «стимул–артефакт–окружение–ответ–метрика» для спецификации NFR | knowledge/system-design/nfr.md | high | confirmed-by-knowledge-base |
| 9 | Числовые ориентиры в примерах (пороги долей, времена обработки) — учебные иллюстрации, зависят от окружения | final.md, «Примечания честности» | n/a | учебная иллюстрация — подтвердить уместность |
| 10 | Сквозной кейс DriveShare (≈200 авто, 3 города, 8 человек команды) — вымышленные параметры учебного кейса | specs/syllabus.md (учебный кейс), final.md | n/a | художественное допущение — подтвердить уместность |

## Правила заполнения
- `confirmed-by-knowledge-base` — источник найден в `knowledge/**`; человек подтверждает корректность интерпретации.
- `pending-human` — внешний факт без файла-источника или атрибуция, требующая проверки по первоисточнику.

## Итог
- [ ] Все пункты проверены человеком, замечаний нет → final.md может быть представлен к утверждению
- [ ] Есть замечания → правки в final.md/practice, повторная проверка
- Ответственный: ______  Дата: ______
- **human verdict отсутствует — документ остаётся кандидатом**
