Шаблон задачи для генерации одной лекции.

Формат:

# Task: Lesson {номер} — {название}

## Agent Mode

{например, Lesson Writer}

## Input Files

- specs/lessons/lesson-{номер}.spec.md
- templates/lesson.md
- knowledge/glossary.md
- ...

## Output Files

- content/lectures/{папка}/brief.md
- content/lectures/{папка}/outline.md
- content/lectures/{папка}/draft.md

## Constraints

- не писать финальную версию без review;
- использовать русский язык;
- не выдумывать факты;
- не углубляться в код.

## Definition of Done

- созданы необходимые файлы;
- соблюдены обязательные секции;
- пройдена проверка по review-checklist;
- нет противоречий со спецификацией.
