---
title: Мигаючий світлодіод
slug: blink
lang: uk
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

<!-- step:intro -->
# Мета
Навчитись керувати світлодіодом на Arduino та змусити його мигати.

## Тема
Цифрові виходи

## Що навчимось
- Підключати світлодіод до цифрового піна
- Використовувати `pinMode()` та `digitalWrite()`
- Працювати з `delay()` у головному циклі

<!-- step:1
timer: 60
actions:
  - id: hint
    unlock: immediate
    hint: |
      **Підказка:** Резистор захищає світлодіод від перегорання. Без нього через LED проходить занадто великий струм.
  - id: know_answer
    unlock: next
-->
## Крок 1: Компоненти та підключення

### Необхідні компоненти
- Arduino Uno або сумісна плата
- Світлодіод (будь-якого кольору)
- Резистор 220 Ом
- Макетна плата
- З'єднувальні дроти

### Схема підключення
1. Підключіть довгу ніжку світлодіода (анод) до цифрового піна 13 через резистор 220 Ом.
2. Підключіть коротку ніжку (катод) до GND.

![Схема підключення світлодіода](/content/assets/img/arduino_blink.png)

<!-- step:2
timer: 90
actions:
  - id: hint
    unlock: immediate
    hint: |
      Пам'ятайте: функція `setup()` виконується один раз при старті, а `loop()` — безкінечно.
  - id: dont_understand
    unlock: timer
    hint: |
      **Пояснення коду:**
      - `pinMode(ledPin, OUTPUT)` — встановлює пін як вихід
      - `digitalWrite(ledPin, HIGH)` — вмикає світлодіод (5V)
      - `delay(1000)` — чекає 1 секунду
-->
## Крок 2: Написання коду

```arduino
const int ledPin = 13;

void setup() {
  pinMode(ledPin, OUTPUT);
}

void loop() {
  digitalWrite(ledPin, HIGH);
  delay(1000);
  digitalWrite(ledPin, LOW);
  delay(1000);
}
```

<!-- step:3
timer: 30
actions:
  - id: know_answer
    unlock: next
-->
## Крок 3: Експерименти та висновок

Спробуйте змінити значення затримки, щоб світлодіод мигав швидше або повільніше.

Вітаємо! Ви створили свій перший проект з Arduino.
