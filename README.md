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

| Date | Domain | Paper | Tags | Core Value | ⚠️ Red Flags |
|:-----|:-------|:------|:-----|:-----------|:------------|
| 2026-05-07 | Heat Treatment · Furnace | [GA-BP HEC Furnace (2025)](docs/heat-treatment/furnace/2025_GABP-FurnaceHEC.md) | `#GA-BP` `#BPNN` `#HEC` `#SRRF` `#EnergyPrediction` | 以 GA 暖啟動優化 BP 初始權重，首次應用於鋼鐵再加熱爐每噸能耗（HEC）預測，MAPE 從 9.76% 降至 5.25% | 出爐溫度為後驗輸入（數據洩漏）；僅與原始 BP 對比（稻草人基準線） |
| 2026-05-06 | Heat Treatment · Furnace | [Multi-Mode MPC Billet Furnace (2023)](docs/heat-treatment/furnace/2023_MultiModeMPC-Furnace.md) | `#MPC` `#VirtualSensor` `#MultiMode` `#LPV` | 三模式 LPV-QP MPC 統一覆蓋加熱、保溫、過渡全爐況，搭配虛擬感測器實現無縫模式切換 | 僅 N=12 能耗週期即聲稱節能 2%，驗證窗口過短 |
| 2026-05-05 | Metal Processing · Milling | [PrecisionPINN-ABKDE (2026)](docs/metal-processing/milling/2026_PrecisionPINN-ABKDE.md) | `#PINN` `#Milling` `#UQ` | 以自適應帶寬核密度估計（ABKDE）為不確定性權重嵌入 PINN，預測銑削表面粗糙度並提供信賴區間 | 訓練集僅 64 筆，過擬合風險極高 |
| 2026-05-05 | Metal Processing · Lathe | [Hybrid PINNs Heavy-Duty Lathe (2026)](docs/metal-processing/lathe/2026_HybridPINNs-Lathe.md) | `#PINN` `#Lathe` `#Ensemble` | 三模型（PINNs + 數據驅動）集成預測重型車床熱致 Z 軸定位誤差，融合物理約束與量測數據 | 7 點量測配合 6 階多項式，完全過擬合；無跨工況泛化驗證 |
| 2026-05-05 | Heat Treatment · Furnace | [Pusher Furnace Adaptive MPC (2017)](docs/heat-treatment/furnace/2017_PusherFurnace-MPC.md) | `#MPC` `#VirtualSensor` `#Furnace` | 雙層自適應 LPV-MPC 控制推鋼式加熱爐出口溫度，虛擬感測器補償熱電偶盲區 | 基準線為固定增益控制器（過時）；僅 15 小時連續驗證 |

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
