# Research Paper Notes Hub

> 快速論文情報系統，將每篇論文轉化為可追溯、可複用的工程洞察。  
> Beyond summaries — critical analysis, red-flag detection, and practical deployment assessment.

---

## 🗂 Domain Index

| Domain | Sub-domain | Papers |
|--------|------------|:------:|
| [Metal Processing 金屬加工](docs/metal-processing/) | [Milling 銑削](docs/metal-processing/milling/) | 1 |
| [Metal Processing 金屬加工](docs/metal-processing/) | [Lathe / Turning 車床](docs/metal-processing/lathe/) | 1 |
| [Heat Treatment 熱處理](docs/heat-treatment/) | [Reheating Furnace 加熱爐](docs/heat-treatment/furnace/) | 1 |

---

## 📋 Latest Feed

| Date | Domain | Paper | Tags | Core Value |
|:-----|:-------|:------|:-----|:-----------|
| 2026-05-07 | Heat Treatment · Furnace | [GA-BP HEC Furnace (2025)](docs/heat-treatment/furnace/2025_GABP-FurnaceHEC.md) | `#GA-BP` `#BPNN` `#HEC` `#SRRF` `#EnergyPrediction` | GA warm-starts BP weights for furnace energy prediction; tapping-temp leakage & straw-man baseline red flags |
| 2026-05-06 | Heat Treatment · Furnace | [Multi-Mode MPC Billet Furnace (2023)](docs/heat-treatment/furnace/2023_MultiModeMPC-Furnace.md) | `#MPC` `#VirtualSensor` `#MultiMode` `#LPV` | 3-mode LPV-QP for all furnace conditions; N=12 energy periods for 2% savings claim — cherry-pick red flag |
| 2026-05-05 | Metal Processing · Milling | [PrecisionPINN-ABKDE (2026)](docs/metal-processing/milling/2026_PrecisionPINN-ABKDE.md) | `#PINN` `#Milling` `#UQ` | Uncertainty-weighted PINN for surface roughness; 64-sample regime, overfitting red flag |
| 2026-05-05 | Metal Processing · Lathe | [Hybrid PINNs Heavy-Duty Lathe (2026)](docs/metal-processing/lathe/2026_HybridPINNs-Lathe.md) | `#PINN` `#Lathe` `#Ensemble` | Three-model ensemble for Z-axis error; 7-point + 6th-order polynomial = full overfit |
| 2026-05-05 | Heat Treatment · Furnace | [Pusher Furnace Adaptive MPC (2017)](docs/heat-treatment/furnace/2017_PusherFurnace-MPC.md) | `#MPC` `#VirtualSensor` `#Furnace` | Two-layer LPV-MPC for billet reheating; straw-man baseline, 15-hour cherry-pick |

---

## 🧭 Domain Navigation

### Metal Processing (金屬加工)
- **Scope:** Turning, Milling, Grinding, and other subtractive processes
- **Core pain points:** Tool wear · Cutting force prediction · Surface roughness · Chatter monitoring
- **Sub-domains:**
  - [Milling (銑削)](docs/metal-processing/milling/) — 5-axis, micro-milling, surface quality
  - [Lathe / Turning (車床)](docs/metal-processing/lathe/) — CNC precision, positioning error, thermal deformation
  - Grinding (磨削) — *TBD*
  - Forming (成形加工) — *TBD*

### Heat Treatment (熱處理)
- **Scope:** Quenching, tempering, reheating furnaces, phase transformation control
- **Core pain points:** Temperature field control · Energy optimization · Material structure prediction · CCT/TTT curves
- **Sub-domains:**
  - [Reheating Furnace (加熱爐)](docs/heat-treatment/furnace/) — billet heating, MPC, virtual sensors
  - Quenching (淬火) — *TBD*
  - Tempering (回火) — *TBD*

---

## 📁 Repository Structure

```
Research_Paper_Notes_Hub/
│
├── docs/                          # Paper notes, organized by domain > sub-domain
│   ├── metal-processing/
│   │   ├── milling/
│   │   └── lathe/
│   └── heat-treatment/
│       └── furnace/
│
└── images/                        # Figures, tables, equations — one subfolder per paper
    ├── metal-processing/
    │   ├── PrecisionPINN-ABKDE_2026/
    │   └── HybridPINNs-Lathe_2026/
    └── heat-treatment/
        └── PusherFurnace-MPC_2017/
```
