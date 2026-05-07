---
title: "Full paper title here"
year: YYYY
domain: metal-processing | heat-treatment | ...
sub-domain: milling | lathe | furnace | ...
tags: ["Tag1", "Tag2", "Tag3"]
journal: "Journal or Conference Name (Year, IF if known)"
authors: "Author1, Author2, ..."
institution: "Institution Name"
paper_url: "https://doi.org/..."
code_url: "N/A | https://github.com/..."
added: "YYYY-MM-DD"
images: "images/{domain}/{Slug}_{YYYY}/"
---

# [YYYY] Short Descriptive Paper Title

## 基礎資訊 Basic Information

| 欄位 | 內容 |
|------|------|
| 期刊 / 會議 | Journal or Conference, Year (IF: X.X / QN) |
| 作者與單位 | Author1, Author2 @ Institution Name |
| 論文網址 | [doi.org/...](https://doi.org/...) |
| 原始碼 / 實作 | N/A |
| 技術關鍵字 | `#Tag1` `#Tag2` `#Tag3` |

---

## 研究摘要 Research Summary

> **一句話核心：** [One sentence: what problem does this solve, and what is the key mechanism?]

[2-3 paragraphs. Cover: (1) the pain point being addressed, (2) the proposed solution at a high level, (3) how it differs from existing approaches. Use the framing "其技術機制在學術上可被視為一個..." to describe the technical essence.]

### 核心方法論拆解 Core Methodology

1. **[Module / Step Name]** — [What it does, why it is needed, and what inputs/outputs it has]
2. **[Module / Step Name]** — [...]
3. **[Module / Step Name]** — [...]

---

## 實務分析 Practical Analysis

### 資料處理流程 Data Pipeline

[Describe the full data flow: raw sensor/data sources → preprocessing steps → feature engineering → model input format → model output. Mention key hyperparameters (sampling rate, window size, normalization). Reference the main architecture figure.]

![圖 N. 架構圖或流程圖](../../../images/{domain}/{Slug}_{YYYY}/{Slug}_FigN_Description.png)

### 落地瓶頸與風險 Deployment Risks

1. **[Risk Category, e.g., Numerical Stability / Computational Overhead / Sensor Dependency]** — [Describe the specific failure mode and the conditions under which it manifests in a production environment]
2. **[Risk Category]** — [...]
3. **[Risk Category]** — [...]

---

## 落地性評析 Critical Assessment

### 實驗與數據分析 Experimental Scrutiny

- **紅旗 Red Flags:** [Cherry-picking: short eval windows, excluded key variables. Overfitting: complex model on tiny dataset. State sample count explicitly.]
- **基準線審查 Baseline Scrutiny:** [Are comparison models SOTA? Are baselines appropriate for the task? Identify straw-man comparisons.]
- **數據充分性 Data Adequacy:** [How many samples? Is the dataset representative of real operating conditions? Were edge cases (tool wear, material variation, downtime) tested?]

![表 N. 比較結果或消融實驗](../../../images/{domain}/{Slug}_{YYYY}/{Slug}_TableN_Description.png)

### 未來工作建議 Future Work

**理論貢獻評估：**
[Evaluate: how much of the performance gain actually comes from the novel contribution vs. engineering tricks (ensembling, more data, better baselines)? Quote ablation results to support your claim.]

**工程優化建議：**

- **[What to remove / simplify]** — [Why it is unnecessary or problematic]
- **技術替代 Alternative techniques:** [Recommend specific algorithms better suited to the task — e.g., GPR for small data + UQ, B-PINNs for physics + uncertainty, NMPC for nonlinear control]
