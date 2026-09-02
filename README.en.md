<!-- LANG_START -->
🇷🇺 [Русская версия](README.md)
<!-- LANG_END -->

<!-- STATS_START -->
<!-- auto-updated by GitHub Actions · 2026-09-02 19:18 UTC -->

[![Views local](https://img.shields.io/badge/Views_local-289-ff6900?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
[![Views GitHub](https://img.shields.io/badge/Views_GitHub-1-ff6900?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
[![Unique visitors](https://img.shields.io/badge/Unique-1-blue?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
[![Clones](https://img.shields.io/badge/Clones-10-purple?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
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
<!-- auto-updated by GitHub Actions · 2026-09-02 19:18 UTC -->

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
<summary><b>Open issues</b></summary>


<p align="center">
  <b>No open issues.</b><br>
  <sub>The service issue <code>views-counter</code> is hidden from the list.</sub>
</p>


</details>

<p>
  <a href="https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/issues/new/choose">Create new issue</a> ·
  <a href="https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/issues">All issues</a>
</p>

<!-- ISSUES_END -->

## Bitmain APW7 Voltage Mod

![APW7 board](https://raw.githubusercontent.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/main/Full.jpg)

![APW7 board min](https://raw.githubusercontent.com/gooog1111/bitmain-apw7-voltage-mod-fan7688/main/Min.jpg)

---

## # Equipment

- PSU: Bitmain APW7
- Revision: 4 MOSFETs (secondary rectifier)
- Controller: FAN7688 (SOP-16)
- Leg 4: FB (feedback input)

> Applicable ONLY to the 4 MOSFET version shown in the photo.

---

## # Purpose

Increasing the output voltage from **~12.3 V to ~14.0 V**.

---

## # Standard feedback divider

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
Measured: **~12.3 V**

---

## # Formula

Vout = Vref × (1 + R86 / R87)

Actually measured:
Vref ≈ 2.412 V

---

## # Estimated values
```
| R86   | Выход   |
| 8.2k  | ~12.3 В |
| 9.1k  | ~13.4 В |
| 9.31k | ~13.6 В |
| 9.53k | ~13.9 В |
| 9.6k  | ~14.0 В |
```

---

## # Voltage limits

- Minimum: **12.3 V**
- Maximum stable: **13.9–14.0 V**
- Above → **OVP protection is triggered (shutdown)**

---

## # Fixed resistor mod

Replace:

R86: 8.2k → 9.1k – 9.6k

Recommended:

- 9.1k → safe
- 9.53k → close to maximum
- 9.6k → practical maximum

---

## Adjustable option (trimmer resistor)

## # Connection

![Подключение](wiring.jpg)

- Red - +12V
- Yellow - GND
- Blue - FB (leg 4 FAN7688)

---

## # Implementation

R86 = 8.2k + trim resistor 2k

---

## # Actual behavior (important)- Reducing resistance → **no effect (~12.3 V remains)**
- Increased resistance:
  - voltage increases normally
  - stable up to **13.9–14.0 V**
- Higher → **BP goes into defense**

---

## # Practical range
```
| Общее R86 | Выход       |
| 8.2k      | 12.3 В      |
| 9.1k      | 13.3–13.4 В |
| 9.5–9.6k  | 13.9–14.0 В |
| >9.7k     | Защита      |
```

---

## # Important Notes

- Adjustment works **up only**
- Hard OVP threshold (~14 V)
- Adjust voltage under load
- Output capacitors are often rated at **16V**
- Higher voltage increases the load on:
  - rectifiers
  - capacitors
  - secondary winding of the transformer
