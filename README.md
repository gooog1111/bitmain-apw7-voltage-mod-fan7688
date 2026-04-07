Bitmain APW7 Voltage Mod (FAN7688, 4-MOSFET Version)

EN

Hardware

- PSU: Bitmain APW7
- Version: 4 MOSFET secondary (simplified variant)
- Controller: FAN7688
- Pin 4: FB (feedback input)

---

Purpose

Increase output voltage from ~12.3V to ~14–15V.

---

Original Feedback Divider

+12V
  |
 R86 = 8.2k (822)
  |
  +-----> FB (pin 4)
  |
 R87 = 2.0k (30B)
  |
 GND

Output: ~12.3V

---

Modification

Replace:

- R86: 8.2k → 10k (103)

---

Result

R86| Output
8.2k| ~12.3V
9.1k| ~13.3V
10k| ~14.6V
10.5k| ~15.0V

---

Formula

Vout = 2.4 × (1 + R86 / R87)

---

Verified Connections

- FAN7688 pin 4 → R86 → +12V
- FAN7688 pin 4 → R87 → GND

---

Notes

- Do not modify R87
- Step-by-step voltage increase
- Check capacitor rating (typically 16V)

---

RU

Оборудование

- БП: Bitmain APW7
- Версия: 4 MOSFET (упрощённая вторичка)
- Контроллер: FAN7688
- Вывод 4: FB (обратная связь)

---

Назначение

Повышение напряжения с ~12.3В до ~14–15В.

---

Штатный делитель

+12V
  |
 R86 = 8.2k (822)
  |
  +-----> FB (pin 4)
  |
 R87 = 2.0k (30B)
  |
 GND

Выход: ~12.3 В

---

Модификация

Заменить:

- R86: 8.2k → 10k (103)

---

Результат

R86| Напряжение
8.2k| ~12.3 В
9.1k| ~13.3 В
10k| ~14.6 В
10.5k| ~15.0 В

---

Формула

Vout = 2.4 × (1 + R86 / R87)

---

Проверенные соединения

- FAN7688 pin 4 → R86 → +12V
- FAN7688 pin 4 → R87 → GND

---

Примечания

- R87 не изменять
- Повышать напряжение поэтапно
- Проверить конденсаторы (обычно 16 В)

---
