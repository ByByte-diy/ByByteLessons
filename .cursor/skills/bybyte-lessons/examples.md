# ByByte Lessons — еталонні приклади

Методичні критерії до змісту кроків: [methodology.md](methodology.md).

Після міграції на `course_id` у frontmatter еталон stepped-уроків має жити лише за шляхом курсу. Зразок розмітки кроків:

| Мова | Канонічний шлях (ціль) | Зразок stepped-розмітки (оновити course_id) |
|------|------------------------|---------------------------------------------|
| uk | `content/uk/arduino-basics/beginner/blink.md` | `content/uk/arduino/beginner/blink.md` |
| en | `content/en/arduino-basics/beginner/blink.md` | `content/en/arduino/beginner/blink.md` |

При створенні або рефакторингу:

1. Скопіюй структуру кроків з uk/en `blink` у `arduino/beginner/`.
2. Додай `course_id`, `course`, вирівняй шлях під `arduino-basics`.
3. Видали застарілі дублікати (наприклад, article-версії без stepped).

## Що перевірити в еталоні

- Intro: мета, тема, список навичок
- Крок 1: компоненти + схема; `hint` про резистор; `know_answer`
- Крок 2: код; `hint` про setup/loop; `dont_understand` з поясненням рядків
- Крок 3: експеримент + висновок; `know_answer`

## Контент, який треба перевести на stepped

`content/uk/bybyte-nano/beginner/bybyte_nano_start.md` — article-формат. Нові уроки Nano пиши одразу stepped; цей файл мігруй окремим завданням (розбиття на `step:intro`, завдання 1/2, домашка, помилки — окремі кроки з actions).
