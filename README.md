Bitmain APW7 Voltage Mod (FAN7688, 4-MOSFET)

[![Stars](https://img.shields.io/github/stars/gooog1111/bitmain-apw7-voltage-mod-fan7688?style=social)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
![views](https://komarev.com/ghpvc/?username=gooog1111&repo=bitmain-apw7-voltage-mod-fan7688)

---

![APW7 board](https://raw.githubusercontent.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/main/Full.jpg)

---

- [English](#English)
- [Русский](#Русский)

---

## English

Hardware

- PSU: Bitmain APW7
- Revision: 4-MOSFET secondary rectifier version
- Controller: FAN7688 (SOP-16)
- Pin 4: FB (feedback input)

«This information applies to the APW7 4-MOSFET revision shown in the photo and not match other APW7 revisions.»

---

Purpose

Increase output voltage from ~12.3V to ~13–14V (car audio use).

---

Board Photo

"APW7 board"

Feedback divider R86 / R87 identified

---

Original Feedback Divider

```
+12V
  |
 R86 = 8.2k (822)
  |
  +-----> FB (pin 4)
  |
 R87 = 2.0k (30B)
  |
 GND
```

Measured output: ~12.3V

---

Modification

Replace:

- R86: 8.2k → 10k (103)

---

Result
```
R86   | Output
8.2k  | ~12.3V (measured)
9.1k  | ~13.3V (calculated)
10k   | ~14.6V (not work)
```
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
- Increase voltage step-by-step
- Check output capacitors (typically 16V)
- Higher voltage increases stress on components

---

## Русский

Оборудование

- БП: Bitmain APW7
- Ревизия: вторичная часть на 4 MOSFET
- Контроллер: FAN7688 (SOP-16)
- Вывод 4: FB (обратная связь)

«Данные относятся к показанной на фото ревизии APW7 на 4 MOSFET и не совпадают с другими версиями.»

---

Назначение

Повышение выходного напряжения с ~12.3В до ~13–14В (автозвук).

---

Фото платы

"APW7 board"

Определён делитель обратной связи R86 / R87

---

Штатный делитель
```
+12V
  |
 R86 = 8.2k (822)
  |
  +-----> FB (pin 4)
  |
 R87 = 2.0k (30B)
  |
 GND
```
Измерено: ~12.3 В

---

Модификация

Заменить:

- R86: 8.2k → 10k (103)

---

Результат
```
R86   | Напряжение
8.2k  | ~12.3 В (измерено)
9.1k  | ~13.3 В (расчёт)
10k   | ~14.6 В (не работает)
```
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
- При увеличении напряжения растёт нагрузка на компоненты

---
