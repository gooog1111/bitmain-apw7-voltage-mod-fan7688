# Bitmain APW7 Voltage Mod (FAN7688, 4-MOSFET)

[![Stars](https://img.shields.io/github/stars/gooog1111/bitmain-apw7-voltage-mod-fan7688?style=social)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
![views](https://komarev.com/ghpvc/?username=gooog1111&repo=bitmain-apw7-voltage-mod-fan7688)

---

![APW7 board](https://raw.githubusercontent.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/main/Full.jpg)

---

- [English](#english)
- [Русский](#русский)

---

## English

### Hardware

- PSU: Bitmain APW7
- Revision: 4-MOSFET secondary rectifier version
- Controller: FAN7688 (SOP-16)
- Pin 4: FB (feedback input)

> This information applies to the APW7 4-MOSFET revision shown in the photo. Other APW7 revisions may use a different feedback circuit.

---

### Purpose

Increase the output voltage from the stock **~12.3 V** to approximately **13.0–14.0 V** for car audio use.

---

### Board Photo

![APW7 board](https://raw.githubusercontent.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/main/Min.jpg)

Feedback divider **R86 / R87** identified.

---

### Original Feedback Divider

```text
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

Measured stock output voltage: **~12.3 V**.

---

### Voltage Limits

- **Minimum voltage:** ~12.3 V with the stock resistor value.
- **Practical maximum voltage:** **13.9–14.0 V**.
- Above approximately **14.0 V**, the PSU enters protection mode.

> Do not use 10k for R86 if stable operation is required. With this divider it calculates to approximately 14.47 V, which is above the protection threshold.

---

### Modification

Replace **R86** only.

Recommended values:

- **9.1k** — safe increase, approximately 13.39 V.
- **9.53k–9.6k** — near maximum, approximately 13.90–13.99 V.

Do **not** modify R87.

---

### Calculated R86 Values

Calculation is based on the measured stock voltage:

```text
Vref = 12.3 / (1 + 8.2k / 2.0k) = ~2.412 V
Vout = Vref × (1 + R86 / R87)
R87 = 2.0k
```

| R86 value | Calculated output | Status |
|---:|---:|---|
| 8.2k | ~12.30 V | Stock, measured |
| 9.1k | ~13.39 V | Safe |
| 9.31k | ~13.64 V | Safe |
| 9.53k | ~13.90 V | Near maximum |
| 9.6k | ~13.99 V | Maximum practical value |
| 9.76k | ~14.18 V | May trigger protection |
| 10k | ~14.47 V | Triggers protection / not recommended |

---

### Formula

```text
Vout = Vref × (1 + R86 / R87)
R86 = R87 × (Vout / Vref - 1)
```

For this PSU, using the measured stock voltage:

```text
Vref ≈ 2.412 V
R87 = 2.0k
```

Examples:

```text
R86 for 13.9 V = 2.0k × (13.9 / 2.412 - 1) ≈ 9.53k
R86 for 14.0 V = 2.0k × (14.0 / 2.412 - 1) ≈ 9.61k
```

---

### Verified Connections

- FAN7688 pin 4 → R86 → +12V
- FAN7688 pin 4 → R87 → GND

---

### Notes

- Increase voltage step-by-step.
- Check output capacitors. They are often rated for 16 V.
- Higher voltage increases stress on rectifiers, capacitors and transformer secondary circuitry.
- Measure the output voltage under load.
- The protection threshold may vary slightly between PSU revisions.

---

## Русский

### Оборудование

- БП: Bitmain APW7
- Ревизия: вторичная часть на 4 MOSFET
- Контроллер: FAN7688 (SOP-16)
- Вывод 4: FB (вход обратной связи)

> Данные относятся к показанной на фото ревизии APW7 на 4 MOSFET. В других версиях APW7 схема обратной связи может отличаться.

---

### Назначение

Повышение выходного напряжения со штатных **~12,3 В** примерно до **13,0–14,0 В** для автозвука.

---

### Фото платы

![APW7 board](https://raw.githubusercontent.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/main/Min.jpg)

Определён делитель обратной связи **R86 / R87**.

---

### Штатный делитель

```text
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

Измеренное штатное выходное напряжение: **~12,3 В**.

---

### Пределы напряжения

- **Минимальное напряжение:** ~12,3 В со штатным номиналом.
- **Практический максимум:** **13,9–14,0 В**.
- При напряжении выше примерно **14,0 В** блок питания уходит в защиту.

> Не рекомендуется ставить 10k вместо R86 для стабильной работы. С этим делителем расчётное напряжение получается около 14,47 В, что выше порога защиты.

---

### Модификация

Заменять только **R86**.

Рекомендуемые номиналы:

- **9.1k** — безопасное повышение, примерно 13,39 В.
- **9.53k–9.6k** — около максимума, примерно 13,90–13,99 В.

**R87 не изменять.**

---

### Расчёт номиналов R86

Расчёт сделан по измеренному штатному напряжению:

```text
Vref = 12.3 / (1 + 8.2k / 2.0k) = ~2.412 В
Vout = Vref × (1 + R86 / R87)
R87 = 2.0k
```

| Номинал R86 | Расчётное напряжение | Статус |
|---:|---:|---|
| 8.2k | ~12,30 В | Штатно, измерено |
| 9.1k | ~13,39 В | Безопасно |
| 9.31k | ~13,64 В | Безопасно |
| 9.53k | ~13,90 В | Около максимума |
| 9.6k | ~13,99 В | Практический максимум |
| 9.76k | ~14,18 В | Возможен уход в защиту |
| 10k | ~14,47 В | Уходит в защиту / не рекомендуется |

---

### Формула

```text
Vout = Vref × (1 + R86 / R87)
R86 = R87 × (Vout / Vref - 1)
```

Для этого блока, с учётом измеренного штатного напряжения:

```text
Vref ≈ 2.412 В
R87 = 2.0k
```

Примеры:

```text
R86 для 13.9 В = 2.0k × (13.9 / 2.412 - 1) ≈ 9.53k
R86 для 14.0 В = 2.0k × (14.0 / 2.412 - 1) ≈ 9.61k
```

---

### Проверенные соединения

- FAN7688 pin 4 → R86 → +12V
- FAN7688 pin 4 → R87 → GND

---

### Примечания

- Повышать напряжение поэтапно.
- Проверить выходные конденсаторы. Часто они рассчитаны на 16 В.
- При увеличении напряжения растёт нагрузка на выпрямители, конденсаторы и вторичную часть трансформатора.
- Измерять выходное напряжение лучше под нагрузкой.
- Порог защиты может немного отличаться между ревизиями БП.

---
