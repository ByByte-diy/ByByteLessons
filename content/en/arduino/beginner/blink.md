---
title: Blinking LED
slug: blink
lang: en
platforms: 
  - arduino
level: beginner
tags: 
  - led
  - digital outputs
published: true
version: 1.0.0
description: Classic example with a blinking LED for Arduino.
steps:
  mode: stepped
---

<!-- step:intro -->
# Goal
Learn how to control an LED on Arduino and make it blink.

## Topic
Digital outputs

## What you'll learn
- Connect an LED to a digital pin
- Use `pinMode()` and `digitalWrite()`
- Work with `delay()` in the main loop

<!-- step:1
timer: 60
actions:
  - id: hint
    unlock: immediate
    hint: |
      **Hint:** The resistor protects the LED from burning out. Without it, too much current flows through the LED.
  - id: know_answer
    unlock: next
-->
## Step 1: Components and wiring

### Required components
- Arduino Uno or compatible board
- LED (any color)
- 220 Ohm resistor
- Breadboard
- Jumper wires

### Connection diagram
1. Connect the long leg of the LED (anode) to digital pin 13 through a 220 Ohm resistor.
2. Connect the short leg (cathode) to GND.

![LED Connection Diagram](/content/assets/img/arduino_blink.png)

<!-- step:2
timer: 90
actions:
  - id: hint
    unlock: immediate
    hint: |
      Remember: `setup()` runs once at startup, and `loop()` runs repeatedly.
  - id: dont_understand
    unlock: timer
    hint: |
      **Code explanation:**
      - `pinMode(ledPin, OUTPUT)` — sets the pin as an output
      - `digitalWrite(ledPin, HIGH)` — turns the LED on (5V)
      - `delay(1000)` — waits 1 second
-->
## Step 2: Write the code

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
## Step 3: Experiments and conclusion

Try changing the delay values to make the LED blink faster or slower.

Congratulations! You have created your first Arduino project.
