# Bitmain APW7 Voltage Mod (FAN7688, 4-MOSFET)

[![Stars](https://img.shields.io/github/stars/gooog1111/bitmain-apw7-voltage-mod-fan7688?style=social)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
![views](https://komarev.com/ghpvc/?username=gooog1111&repo=bitmain-apw7-voltage-mod-fan7688)

---

![APW7 board](https://raw.githubusercontent.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/main/Full.jpg)

---

## Adjustable Mod (Trimmer Method)

### Wiring Example

![Wiring example](wiring.jpg)

**Connections:**

- Red — +12V
- Yellow — GND
- Blue — FB (pin 4 FAN7688)

---

### Implementation

Use:

- 8.2k (fixed) + 2k trimmer

---

### Behavior (Real Test)

- Lowering resistance below stock → **no change (~12.3 V)**
- Increasing resistance:
  - stable up to **13.9–14.0 V**
- Above ~14.0 V → **PSU enters protection**

---

### Practical Range

| Total R86 | Output |
|---:|---:|
| 8.2k | ~12.3 V |
| 9.1k | ~13.3–13.4 V |
| 9.5–9.6k | ~13.9–14.0 V |
| >9.7k | Protection |

---

### Notes

- Regulation works only upwards
- Hard OVP threshold (~14 V)
- Adjust under load

---

## Русский

### Регулируемый вариант

### Пример подключения

![Пример подключения](wiring.jpg)

- Красный — +12V
- Жёлтый — GND
- Синий — FB (pin 4)

---

### Поведение

- Ниже номинала → не меняется (~12.3 В)
- До 13.9–14.0 В — стабильно
- Выше → защита

---
