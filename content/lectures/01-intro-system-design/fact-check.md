# Fact-check Лекции 1 — реестр проверяемых утверждений

> **Статус: НЕ ЗАВЕРШЁН.** По правилам курса fact-check завершает только человек.
> AI подготовил реестр ключевых утверждений final.md с источниками и уверенностью.
> Статус `confirmed-by-knowledge-base` означает наличие источника в `knowledge/**` — это НЕ вердикт человека.
> Итог: human verdict отсутствует — документ `final.md` остаётся кандидатом.

## Реестр (claim / source / confidence / status)

| № | Утверждение (claim) | Источник (source) | Confidence | Status |
|---|---|---|---|---|
| 1 | System Design — процесс выбора архитектурных компромиссов под бизнес-цели, а не «выбор лучшей технологии» | knowledge/system-design/trade-offs.md, knowledge/system-design/architecture-styles.md | high | confirmed-by-knowledge-base |
| 2 | Закон Конвея: структуры коммуникации организации определяют структуру проектируемых систем | общедостатный факт (Mel Conway, 1968, "How Do Committees Invent?") | high | pending-human |
| 3 | NFR (производительность, надёжность, безопасность) являются архитектурными драйверами и ограничивают выбор решений сильнее, чем FR | knowledge/system-design/nfr.md | high | confirmed-by-knowledge-base |
| 4 | Данные как архитектурное ограничение: модель хранения влияет на границы сервисов и каналы доступа | knowledge/databases/dbms-types.md, knowledge/databases/storage-selection.md | medium | confirmed-by-knowledge-base |
| 5 | SLA — внешнее обязательство перед потребителем, SLO — внутренняя измеримая цель; error budget — производная от разницы | knowledge/system-design/nfr.md (§ «Метрики успеха (SLO/SLA)»), knowledge/glossary.md:90-91; сверить с Google SRE Book | medium | pending-human |
| 6 | C4 Model: Context → Container → Component → Code — четыре уровня детализации | knowledge/system-design/c4-model.md + общедостатная документация Simon Brown (c4model.com) | high | pending-human |
| 7 | ADR фиксирует контекст, решение и последствия; принятые ADR не переписываются, добавляются новые superseding-записи | knowledge/system-design/ADR.md; Michael Nygard, 2011 | high | confirmed-by-knowledge-base |
| 8 | Пример сквозного кейса (ride-hailing, пороги латентности) — учебная иллюстрация, вымышленные числа | final.md, блок «Примечания честности» | n/a | учебная иллюстрация — проверять не требуется, подтвердить уместность |
| 9 | Атрибуция PACELC — Дэниэл Абади (по syllabus и glossary; вариант «Лодейерс» в промте заказчика ошибочен) | specs/syllabus.md, knowledge/glossary.md | high | confirmed-by-knowledge-base |
| 10 | Тезис «итоговый отчёт курса станет ТЗ для реализации в курсе „Базы данных“» | specs/syllabus.md, Лекция 1, «Связь с курсом» | high | confirmed-by-knowledge-base |

## Правила заполнения
- `confirmed-by-knowledge-base` — источник найден в `knowledge/**`; человек всё равно подтверждает корректность интерпретации.
- `pending-human` — внешний/общеизвестный факт без файла-источника или непроверяемое утверждение; закрывает только человек.
- Непроверяемое → переформулировать как учебную иллюстрацию либо удалить.

## Итог
- [ ] Все пункты проверены человеком, замечаний нет → final.md может быть представлен к утверждению
- [ ] Есть замечания → правки в final.md/slides/practice, повторная проверка
- Ответственный: ______  Дата: ______
- **human verdict отсутствует — документ остаётся кандидатом**
