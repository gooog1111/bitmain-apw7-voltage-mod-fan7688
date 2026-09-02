<!-- LANG_START -->
🇬🇧 [English version](README.en.md)
<!-- LANG_END -->

<!-- STATS_START -->
<!-- auto-updated by GitHub Actions · 2026-07-10 15:44 UTC -->

[![Views local](https://img.shields.io/badge/Views_local-288-ff6900?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
[![Views GitHub](https://img.shields.io/badge/Views_GitHub-1-ff6900?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
[![Unique visitors](https://img.shields.io/badge/Unique-1-blue?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
[![Clones](https://img.shields.io/badge/Clones-2115-purple?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
[![Stars](https://img.shields.io/badge/Stars-0-yellow?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/stargazers)
[![Forks](https://img.shields.io/badge/Forks-0-green?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/network/members)
[![Downloads latest release](https://img.shields.io/badge/Downloads_latest_release-0-brightgreen?style=for-the-badge)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/releases/latest)
[![Downloads total assets](https://img.shields.io/badge/Downloads_total_assets-0-brightgreen?style=for-the-badge)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/releases)

<!-- STATS_END -->

<!-- GRAPH_START -->
<p align="center">
  <img src="./traffic-views.png" width="100%" alt="GitHub Traffic">
</p>
<!-- GRAPH_END -->

<!-- ISSUES_START -->
<!-- auto-updated by GitHub Actions · 2026-07-10 15:44 UTC -->

## Issues

<p>
  <a href="https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/issues">
    <img alt="Open issues" src="https://img.shields.io/badge/Open_issues-0-blue?style=for-the-badge&logo=github">
  </a>
  <a href="https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/issues/new/choose">
    <img alt="Create issue" src="https://img.shields.io/badge/Create_issue-new-success?style=for-the-badge&logo=github">
  </a>
</p>

<details open>
<summary><b>Открытые issues</b></summary>


<p align="center">
  <b>Открытых issues нет.</b><br>
  <sub>Служебный issue <code>views-counter</code> скрыт из списка.</sub>
</p>


</details>

<p>
  <a href="https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/issues/new/choose">Создать issue</a> ·
  <a href="https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/issues">Все issues</a>
</p>

<!-- ISSUES_END -->

## Bitmain APW7 Voltage Mod

![APW7 board](https://raw.githubusercontent.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/main/Full.jpg)

![APW7 board min](https://raw.githubusercontent.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/main/Min.jpg)

---

### Оборудование

- БП: Bitmain APW7
- Ревизия: 4 MOSFET (вторичный выпрямитель)
- Контроллер: FAN7688 (SOP-16)
- Нога 4: FB (вход обратной связи)

> Применимо ТОЛЬКО к версии с 4 MOSFET, показанной на фото.

---

### Назначение

Повышение выходного напряжения с **~12.3 В до ~14.0 В**.

---

### Штатный делитель обратной связи

```
+12V
  |
 R86 = 8.2k
  |
  +-----> FB (pin 4)
  |
 R87 = 2.0k
  |
 GND
```
Измерено: **~12.3 В**

---

### Формула

Vout = Vref × (1 + R86 / R87)

Измерено фактически:
Vref ≈ 2.412 В

---

### Расчётные значения
```
| R86   | Выход   |
| 8.2k  | ~12.3 В |
| 9.1k  | ~13.4 В |
| 9.31k | ~13.6 В |
| 9.53k | ~13.9 В |
| 9.6k  | ~14.0 В |
```

---

### Пределы напряжения

- Минимум: **12.3 В**
- Максимум стабильно: **13.9–14.0 В**
- Выше → **срабатывает защита OVP (отключение)**

---

### Мод фиксированным резистором

Замените:

R86: 8.2k → 9.1k – 9.6k

Рекомендуется:

- 9.1k → безопасно
- 9.53k → близко к максимуму
- 9.6k → практический максимум

---

## Регулируемый вариант (подстроечный резистор)

### Подключение

![Подключение](wiring.jpg)

- Красный — +12V
- Жёлтый — GND
- Синий — FB (нога 4 FAN7688)

---

### Реализация

R86 = 8.2k + подстроечный резистор 2k

---

### Реальное поведение (важно)

- Уменьшение сопротивления → **эффекта нет (~12.3 В остаётся)**
- Увеличение сопротивления:
  - напряжение растёт нормально
  - стабильно до **13.9–14.0 В**
- Выше → **БП уходит в защиту**

---

### Практический диапазон
```
| Общее R86 | Выход       |
| 8.2k      | 12.3 В      |
| 9.1k      | 13.3–13.4 В |
| 9.5–9.6k  | 13.9–14.0 В |
| >9.7k     | Защита      |
```

---

### Важные замечания

- Регулировка работает **только вверх**
- Жёсткий порог OVP (~14 В)
- Настраивайте напряжение под нагрузкой
- Выходные конденсаторы часто рассчитаны на **16В**
- Более высокое напряжение увеличивает нагрузку на:
  - выпрямители
  - конденсаторы
  - вторичную обмотку трансформатора
