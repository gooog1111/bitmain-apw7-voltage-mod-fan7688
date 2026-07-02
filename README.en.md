<!-- LANG_START -->
🇷🇺 [Русская версия](README.md)
<!-- LANG_END -->

<div align="center">

<img src="resources/header.svg" alt="Bitmain APW7 Voltage Mod" width="900"/>

</div>





<!-- STATS_START -->
<!-- auto-updated by GitHub Actions · 2026-07-02 00:00 UTC -->

[![Views local](https://img.shields.io/badge/Views_local-83-ff6900?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
[![Views GitHub](https://img.shields.io/badge/Views_GitHub-2-ff6900?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
[![Unique visitors](https://img.shields.io/badge/Unique-1-blue?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
[![Clones](https://img.shields.io/badge/Clones-556-purple?style=for-the-badge&logo=github)](https://github.com/gooog1111/bitmain-apw7-voltage-mod-fan7688)
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
<!-- auto-updated by GitHub Actions · 2026-07-02 00:00 UTC -->

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

- [English](#english)
- [Русский](#русский)

---

## English

## #Hardware

- PSU: Bitmain APW7
- Revision: 4-MOSFET secondary rectifier version
- Controller: FAN7688 (SOP-16)
- Pin 4: FB (feedback input)

> This applies ONLY to the 4-MOSFET version shown in the photo.

---

## #Purpose

Increase output voltage from **~12.3 V up to ~14.0 V**.

---

## #Original Feedback Divider

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

## #Formula

Vout = Vref × (1 + R86 / R87)

Real measured:
Vref ≈ 2.412 V

---

## # Calculated Values
```
| R86   | Output  |
| 8.2k  | ~12.3 V |
| 9.1k  | ~13.4 V |
| 9.31k | ~13.6 V |
| 9.53k | ~13.9 V |
| 9.6k  | ~14.0 V |
```
---

## #Voltage Limits

- Minimum: **12.3 V**
- Maximum stable: **13.9–14.0 V**
- Above → **OVP protection (shutdown)**

---

## #Fixed Resistor Mod

Replace:

R86: 8.2k → 9.1k – 9.6k

Recommended:

- 9.1k → safe
- 9.53k → near max
- 9.6k → maximum practical

---

## Adjustable Mod (Trimmer)

## # Wiring

![Wiring](wiring.jpg)

- Red — +12V
-Yellow—GND
- Blue - FB (pin 4 FAN7688)

---

## # Implementation

R86 = 8.2k + 2k trimmer

---

## # Real Behavior (important)

- Deccreasing resistance → **no effect (~12.3 V stays)**
- Increasing resistance:
  - voltage rises normally
  - stable up to **13.9–14.0 V**
- Above → **PSU enters protection**

---

## # Practical Range
```
| Total R86.    | Output |
| 8.2k          | 12.3 V |
| 9.1k     | 13.3–13.4 V |
| 9.5–9.6k | 13.9–14.0 V |
| >9.7k     | Protection |
```
---

## # Important Notes

- Regulation works **only upward**
- Hard OVP threshold (~14 V)
- Adjust voltage under load
- Output capacitors are often **16V rated**
- Higher voltage increases stress on:
  - rectifiers
  -capacitors
  - transformer secondary

---

## Russian

## # Equipment

- PSU: Bitmain APW7
- Revision: 4 MOSFETs
- Controller: FAN7688
- 4 legs - FB

---

## # Purpose

Increasing voltage from **~12.3 V to ~14.0 V**

---

## # Regular divider

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

Output: **~12.3 V**

---

## # Formula

Vout = Vref × (1 + R86 / R87)

Vref ≈ 2.412 V

---

## # Calculation
```
| R86   | Напряжение |
| 8.2k  | ~12.3 В    |
| 9.1k  | ~13.4 В.   |
| 9.53k | ~13.9 В    |
| 9.6k  | ~14.0 В    |
```
---

## # Limits

- Minimum: 12.3 V
- Maximum: 13.9–14.0 V
- Next → protection

---

## Adjustable option

## # Connection

![Подключение](wiring.jpg)

- Red - 12V
- Yellow - GND
- Blue – FB

---

## # Implementation

8.2k + 2k variable resistor

---

## # Behavior

- Down is not adjustable
- Up to 13.9–14.0 V
- Further protection

---

## # Conclusion

- Adjustment only up
- Hard protection threshold
- Operating maximum ≈ 14 V
