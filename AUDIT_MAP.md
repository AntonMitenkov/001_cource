# AUDIT_MAP — самодиагностика репозитория курса (Этап 0)

Дата аудита: 12.10.2026. Все цифры получены командами в рабочем дереве, а не из промта.

## 1. Объём final-текстов (`wc -m content/lectures/*/final.md`)

Норма: ≥85 000 знаков основного текста на 80 минут (≈1000–1100 знаков/мин).

| Лекция | Знаков в final.md | Оценка минут | Дефект |
|---|---:|---:|---|
| Л1 `01-intro-system-design` | 17 605 | ≈16 мин | ≪ нормы |
| Л2 `02-domain-and-requirements` | 39 264 | ≈36 мин | ≪ нормы + отсутствуют темы syllabus |
| Л3 `03-data-modeling-normalization` | 20 046 | ≈18 мин | ≪ нормы |
| Л4 `04-data-architecture-dbms` | 34 270 | ≈31 мин | ≪ нормы |
| Л5 `05-app-db-interaction-security-tools` | 21 117 | ≈19 мин | ≪ нормы |
| Л6 `06-data-reliability-recovery` | 21 304 | ≈19 мин | ≪ нормы |
| Л7 `07-system-design-final-assembly-peer-review` | 17 951 | ≈16 мин | ≪ нормы |
| Л8 `08-scaling-caching-oltp-olap` | 4 674 | ≈4 мин | пересказ draft + прямая ссылка «как в draft.md» |

## 2. CJK-артефакты (python-сканер `[\u4e00-\u9fff\u3040-\u30ff\uac00-\ud7af]` по всему дереву)

| Файл | Найдено | Характер |
|---|---|---|
| `README.md` (строка 213) | `禁止` | «…оформлять в APA/MLA;禁止 плагиат…» → заменить на «запрещён» |
| `content/lectures/02-domain-and-requirements/draft.md` (стр. 470, 471) | `不接受`, японская фраза в кавычках 「…」 | правки по смыслу («не принимаем „система должна быть быстрой“» → измеримая формулировка) |
| `content/lectures/02-domain-and-requirements/review.md` (стр. 160) | та же цитата внутри описания дефекта | цитируется как артефакт — переписать описание без иероглифов |
| `content/lectures/02-domain-and-requirements/generation-report.md` (стр. 82) | «Было: …」 | зафиксировать факт замены русским текстом |
| `content/lectures/05.../review.md` (стр. 45) | `禁止` в перечислении исправленных вставок | переформулировать без иероглифа |
| `content/lectures/06.../generation-report.md` (стр. 54) | `覆盖` | переформулировать |
| `content/lectures/06.../review.md` | `仲裁提议` (4 символа) | переформулировать |
| `content/lectures/08.../generation-report.md` | `专职` | переформулировать |

В `final.md` лекций CJK нет (скан показал только перечисленные файлы).

## 3. Покрытие темами syllabus (ключевые слова в Л2 final.md)

`grep -ci "Исикав|BABOK|MoSCoW|SMART|5 почему" content/lectures/02-domain-and-requirements/final.md` → **0**.
Сyllabus Л2 требует: диаграмма Исикавы/6M, «5 почему», виды требований BABOK, SMART FR, MoSCoW — всё отсутствует. Практический результат syllabus («Исикава + приоритизированные FR») не проверяется ни в final.md, ни в practice.md.

## 4. Fact-check

- `content/lectures/01-*/fact-check.md` — **отсутствует**;
- `content/lectures/02-*/fact-check.md` — **отсутствует**;
- Л3–Л8 — существуют, но все в статусе «НЕ ВЫПОЛНЕН / протокол» (по правилам проекта так и должно быть до человека; задача — непустой реестр claim/source/confidence/status).

## 5. Статусы vs README

- README §8: «Л8 — ожидает генерации» — **ложь**: пакет Л8 существует (brief→slides, final — кандидат).
- README tree: заявлены несуществующие директории `content/practices/`, `content/cases/`, `content/assessments/`, `content/appendix/`; несуществующие файлы `knowledge/databases/db-interaction.md`, `db-security.md`, `db-tools.md`, весь раздел `knowledge/reliability/` (replication/backups/rpo-rto), весь `knowledge/scaling/` (caching/indexing/data-warehouse-etl/system-design-patterns); `specs/practice-contract.md` (реально — `specs/content-contracts/practice-contract.md`); `knowledge/system-design/adr.md` (реально — `ADR.md`).
- README: шаблоны `peer-review.md`, `architecture-brief.md` заявлены — **отсутствуют** в `templates/`.
- `templates/lesson-task.md.` — имя файла с завершающей точкой (опечатка); ссылок на него в md-файлах нет.
- В `final.md` Л8 двойная формулировка статуса + строка «*(полный текст конспекта — как в draft.md …)*» — нарушение п.4.2 жёстких правил.

## 6. Обязательные секции lesson-contract §1 (13 секций)

Проверка по заголовкам каждого final.md:

| Секция | Л1 | Л2 | Л3 | Л4 | Л5 | Л6 | Л7 | Л8 |
|---|---|---|---|---|---|---|---|---|
| 1.1 Цель | + | + | + | + | + | + | + | + |
| 1.2 LO | + | + | + | + | + | + | + | + |
| 1.3 План | + | + | + | + | + | + | + | **−** |
| 1.4 Hook | + | + | + | + | + | + | + | + |
| 1.5 Теория | + | + | + | + | + | + | + | конспект |
| 1.6 Case | + | + | + | + | + | + | + | конспект |
| 1.7 Управленч. | + | + | + | + | + | + | + | конспект |
| 1.8 Термины | + | + | **−** | + | + | + | + | **−** (отсылка к draft §11) |
| 1.9 Визуальные | + | + | **−** | + | + | + | **−** | **−** |
| 1.10 Anti-pattern | + | + | + | + | + | + | + | конспект |
| 1.11 Практика | + | + | + | + | + | + | отсылка | **−** (отсылка) |
| 1.12 Мостик | + | + | + | + | + | + | + | + |
| 1.13 Вопросы | + | + | + | + | + | + | + | **−** (отсылка к draft §12) |

Дополнительно: у Л2 «Мостик к следующей лекции» описывает тему Л3 как «архитектурные стили» — рассогласовано с syllabus (Л3 = модели данных/нормализация). Тот же дефект унаследован из старого цикла генерации.

## 7. Приоритеты

- **P0**: Л2 — добор тем syllabus (Исикава/5 почему/BABOK/SMART/MoSCoW) + фиксация мостика; Л8 — самодостаточный final; объёмы всех лекций к норме 85k.
- **P0 (чистота)**: устранение CJK во всех файлах; удаление заглушек-ссылок на draft из final-текстов.
- **P1**: README (пути/статусы/禁止), templates (переименование, peer-review, architecture-brief), fact-check Л1/Л2, статусные шапки final.md, синхронизация generation-report и backlog.
- **P2**: GLOSSARY-CONFLICTS.md, межлексические противоречия (денормализация Л3↔Л8), сквозные ссылки, вычитка.

## 8. План работ (коммиты логическими блоками)

1. `fix(audit): add AUDIT_MAP.md` — этот файл.
2. `fix(cjk): remove CJK artifacts from README, L2 draft/review/genreport, L5/L6 review, L6/L8 genreports`.
3. `fix(L2): add Ishikawa, 5 Whys, BABOK, SMART, MoSCoW sections per syllabus; fix bridge to L3`.
4. `rewrite(L8): self-contained final.md per lesson-contract (13 sections, 80 min)`.
5. `expand(L1..L7): bring finals to 80-minute volume` (по одной серии коммитов на лекцию).
6. `fix(readme): truthful paths/statuses; templates: rename lesson-task, add peer-review & architecture-brief`.
7. `add(fact-check): registries for L1, L2; fill claims in existing`.
8. `docs(sync): generation-reports + tasks/backlog after edits`.
9. `fix(quality): GLOSSARY-CONFLICTS.md, denormalization consistency, links`.
10. Verification pass (Этап 5).

## 9. SYLLABUS_ISSUES

На момент аудита фактических ошибок в самом syllabus (несуществующие стандарты/атрибуции) не обнаружено: Event Storming (Brandolini), Исикава, BABOK/IIBA, CAP/PACELC, DDIA/Kleppmann — атрибуции корректны. Файл `SYLLABUS_ISSUES.md` создаётся с нулевым списком и правилом пополнения.
