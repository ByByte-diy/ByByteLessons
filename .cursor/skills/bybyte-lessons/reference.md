# ByByte Lessons — довідник формату

Педагогічні правила (RoboSchool, етапи уроку, план курсу): [methodology.md](methodology.md).

## Публікація (submodule)

1. Уроки комітять у **ByByteLessons**.
2. Головний репозиторій платформи ByByte підключає цей репо як **submodule** (шлях залежить від монорепо; зміни не деплояться, поки submodule не оновлено та не зібрано/задеплоєно головний проєкт).
3. Після змін перевір `published` і версію; чернетки лишай `published: false`.

## Frontmatter — повний приклад

```yaml
---
title: Мигаючий світлодіод
slug: blink
lang: uk
course_id: arduino-basics
course: Основи Arduino
platforms:
  - arduino
level: beginner
tags:
  - світлодіод
  - цифрові виходи
published: true
version: 1.0.0
description: Класичний приклад з мигаючим світлодіодом для Arduino.
steps:
  mode: stepped
---
```

| Поле | Обов’язкове | Примітки |
|------|-------------|----------|
| `title` | так | |
| `slug` | так | `[a-z0-9_-]+` |
| `lang` | так | `uk`, `en` |
| `course_id` | так | kebab-case |
| `course` | так | локалізована назва |
| `platforms` | так | масив рядків |
| `level` | так | |
| `tags` | так | масив, локалізований |
| `published` | так | boolean |
| `version` | так | SemVer |
| `description` | так | 1–2 речення |
| `steps.mode` | так | лише `stepped` |

## Структура стоп-блоків

### Intro

```markdown
<!-- step:intro -->
# Мета
...

## Тема
...

## Що навчимось
- ...
```

Без `timer` / `actions` у коментарі.

### Навчальний крок

```markdown
<!-- step:1
timer: 60
actions:
  - id: hint
    unlock: immediate
    hint: |
      **Підказка:** ...
  - id: know_answer
    unlock: next
-->
## Крок 1: ...

(Тут — **задача** для учня: що зібрати, написати, перевірити.)
```

### Actions

| `id` | Призначення (Рєпкін) | Типовий `unlock` |
|------|----------------------|------------------|
| `hint` | Перша підказка; діагностичне питання (§2.5 methodology) | `immediate` |
| `dont_understand` | Розібраний приклад / пояснення після спроби (§2.9) | `timer` |
| `know_answer` | Перевірка розуміння, не лише «зробив» (§2.12) | `next` |

| `unlock` | Значення |
|----------|----------|
| `immediate` | Доступно одразу на кроці |
| `next` | Відкриває перехід до наступного кроку |
| `timer` | Після закінчення `timer` кроку |

На кроці з кодом зазвичай: `hint` + `dont_understand` + опційно `know_answer` на фінальному підкроці.

Рекомендовані `timer` (сек): просте підключення 45–60; код/налагодження 90–120; рефлексія/експеримент 30–45.

## Шаблон нового уроку

```markdown
---
title: 
slug: 
lang: uk
course_id: 
course: 
platforms:
  - 
level: beginner
tags:
  - 
published: false
version: 1.0.0
description: 
steps:
  mode: stepped
---

<!-- step:intro -->
# Мета

## Тема

## Що навчимось
- 

<!-- step:1
timer: 60
actions:
  - id: hint
    unlock: immediate
    hint: |
      **Підказка:** 
  - id: know_answer
    unlock: next
-->
## Крок 1: 

<!-- step:2
timer: 90
actions:
  - id: hint
    unlock: immediate
    hint: |
      **Підказка:** 
  - id: dont_understand
    unlock: timer
    hint: |
      **Пояснення:** 
  - id: know_answer
    unlock: next
-->
## Крок 2: 

<!-- step:3
timer: 30
actions:
  - id: know_answer
    unlock: next
-->
## Крок 3: 
```

Довгі сюжети (наприклад, курс ByByte Nano) **розбивай на більше кроків**, а не на один файл-статтю.

## Курси в репозиторії (орієнтир)

| `course_id` | `platforms` (типово) | Приклад slug |
|-------------|----------------------|--------------|
| `arduino-basics` | `arduino` | `blink` |
| `bybyte-nano` | `bybyte_nano` | `bybyte_nano_start` |

Новий курс: нова папка `content/{lang}/{course_id}/`, однаковий `course_id` у всіх уроках курсу.

## Версіонування

| Зміна | `version` |
|-------|-----------|
| Друкарські, підказки | patch: `1.0.1` |
| Новий крок, переструктуризація | minor: `1.1.0` |
| Інша мета уроку / slug | major: `2.0.0` + узгодження з платформою |
