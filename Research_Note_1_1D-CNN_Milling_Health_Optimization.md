# 📘 研究論文紀錄：1. Unlocking Dual Utility: 1D-CNN for Milling Tool Health Assessment and Experimental Optimization

---

## 📝 1️⃣ 論文基本資訊  
- **標題**: Unlocking Dual Utility: 1D-CNN for Milling Tool Health Assessment and Experimental Optimization  
- **作者**: Ghazal Farhani 等  
- **發表期刊**: IEEE ACCESS  
- **發表日期**: 2024年5月27日  
- **DOI**: 10.1109/ACCESS.2024.3406262  
- **研究機構**: 加拿大國家研究委員會 (National Research Council Canada)  

---

## 💡 2️⃣ 研究背景與動機  
**刀具磨耗 (Tool Wear)** 在 CNC 銑削加工中會影響工件表面粗糙度並可能損害機器，因此 **剩餘壽命 (RUL, Remaining Useful Life)** 預測對經濟性及安全性至關重要。

### 🔍 傳統的 RUL 預測方法：
1. **經驗型模型 (Experience-based)**：依賴專家知識，但無法有效應對複雜失效模式。  
2. **物理型模型 (Physics-based)**：基於物理機制，但對複雜系統適應性有限，且參數估計誤差大。  
3. **數據驅動型模型 (Data-driven)**：基於歷史數據進行學習，特別適合非線性退化過程。  

---

## 🚀 3️⃣ 研究目標與貢獻  
**本研究提出**：
- 使用 **1D-CNN (一維卷積神經網路)** 進行 **刀具健康狀態分類 (三類標籤：健康、過渡、失效)**。  
- 探索 **1D-CNN 雙重效用 (Dual Utility)**：
  1. **刀具健康狀態評估 (Health Assessment)**  
  2. **實驗參數優化 (Experimental Optimization)**  
- 採用 **Leave-One-Out 交叉驗證 (LOOCV)** 進行模型評估，在數據有限下取得高準確度。  

---

## 📊 4️⃣ 實驗設計與數據處理  
### 🛠️ 實驗設備與資料採集  
- **設備**: 5軸 HURON CNC 銑床  
- **刀具**: Kennametal ADKT103504PDERLCKC725M (2刃, 直徑20mm)  
- **工件**: 4030不鏽鋼 (150mm × 110mm)  
- **感測器**:  
  - Kistler 9255C 三分量動力計 (收集 Fx, Fy, Fz)  
  - Renishaw Bloom 雷射感測器 (量測刀具磨耗)  
- **訊號採樣頻率**: 2000 Hz (NI-LabVIEW)  

### 🏷️ 數據標註 (Labels)  
- 根據刀具磨耗值 (Laser Measurement) 劃分三類：  
  - **健康 (Healthy)**：磨耗 < 30 μm  
  - **過渡 (Transition)**：30 μm ≤ 磨耗 ≤ 70 μm  
  - **失效 (Failure)**：磨耗 > 70 μm  

### ⚙️ 資料預處理 (Data Pre-processing)  
- **去除多餘資料段**：使用滑動視窗偵測空轉段落 (如換刀段)  
- **訊號過濾**：4階 **Butterworth 頻帶通濾波器 (130-135 Hz)** 濾除雜訊  
- **標準化 (Standardization)**：將訊號調整為均值0、標準差1  

---

## 🤖 5️⃣ 1D-CNN模型設計與訓練  
### 🧱 模型架構 (1D-CNN Architecture)  
- **輸入維度**: 三通道 (Fx, Fy, Fz) 力訊號序列  
- **卷積層 (Convolutional Layer)**：多層 1D 卷積 + **ReLU 激活函數**  
- **池化層 (Pooling Layer)**：**Max Pooling** 降維  
- **輸出層 (Output Layer)**：三分類 (健康、過渡、失效)  

### 🏋️ 模型訓練 (Model Training)  
- **框架**: 使用 **Keras (Python)**  
- **批次正規化 (Batch Normalization)**：加快收斂並提升穩定性  
- **超參數調優 (Hyperparameter Tuning)**：  
  - **隨機搜索 (Random Search)** 測試多組組合  
  - 測試多種優化器 (Adam、RMSProp、AdaGrad等)  
  - **Early Stopping** (耐心值=5, 訓練輪數上限=500 Epochs)  
- **交叉驗證法 (Cross-Validation)**：**Leave-One-Out Cross-Validation (LOOCV)**  

---

## 📈 6️⃣ 實驗結果與分析  
### 📊 效能評估 (Performance Metrics)  
- **平均準確度 (Accuracy)**：0.90 ± 0.02  
- **平均精確度 (Precision)**：0.85 ± 0.12  
- **平均召回率 (Recall)**：0.87 ± 0.08  

### 🚀 特徵重要性分析 (Feature Importance)  
- 僅用單一特徵 (Fx, Fy, Fz) 測試模型表現：  
  - ✅ **Fx (X向力)**：模型效果最佳 (關鍵特徵)  
  - ⚠️ **Fy (Y向力)**：部分刀具 (Tool 2, 3) 表現異常，懷疑感測器故障  
  - ❌ **Fz (Z向力)**：無助於區分刀具狀態  

### ⚙️ 採樣頻率對效能影響 (Sampling Rate Analysis)  
- 測試不同採樣間隔 (n = 0, 10, 20, 40, 60) 對模型效能影響：  
  - ✅ **n = 40 (每隔40點取樣)** 效果最佳  
  - 建議 **未來可將採樣頻率由 2000 Hz 降至 50 Hz**，節省資源而效能無明顯下降  

### 🧠 網路深度對效能影響 (Network Depth Analysis)  
- 測試不同 CNN 深度 (3層、5層、10層、20層)：  
  - ✅ **3層 或 5層結構表現最佳**  
  - ⚠️ **20層過深導致過擬合，效果反而變差**  

---

## 📊 7️⃣ 與其他模型比較 (Comparison with SOTA Models)  
### 💥 各模型平均效能比較 (Table 9)  
| **模型 (Model)**                | **準確度 (Accuracy)** | **精確度 (Precision)** | **召回率 (Recall)** | **F1 分數 (F1 Score)** |
|----------------------------|--------------------|---------------------|------------------|------------------|
| **1D-CNN (本研究提出)**     | **0.90 ± 0.02**  | **0.85 ± 0.12**   | **0.87 ± 0.08**  | **0.86 ± 0.09** |
| BiLSTM (雙向LSTM)            | 0.88 ± 0.03       | 0.82 ± 0.11        | 0.83 ± 0.10     | 0.82 ± 0.10     |
| SUBLSTM (CNN+BiLSTM)         | 0.87 ± 0.03       | 0.81 ± 0.12        | 0.84 ± 0.09     | 0.82 ± 0.11     |
| Attention-based LSTM         | 0.89 ± 0.02       | 0.83 ± 0.11        | 0.85 ± 0.09     | 0.84 ± 0.10     |
| Attention-based CNN-LSTM     | 0.88 ± 0.03       | 0.82 ± 0.12        | 0.84 ± 0.10     | 0.83 ± 0.10     |

### 📝 **結果分析重點**：
- ✅ 本研究提出的 **1D-CNN** 效能在 **Accuracy、Precision、Recall、F1 Score** 全面領先  
- ⚠️ 其他模型 (如 BiLSTM, SUBLSTM, Attention-based LSTM) 在 **過渡 (Transition) → 失效 (Failure)** 分類表現偏低  
- ✅ 本研究模型具備：**輕量結構 (3層 1D-CNN)**，在小數據集下不易過擬合且效能高  

---

## 🧩 8️⃣ SOTA 模型「過渡 (Transition)」分類偏低原因分析  
### ⚠️ **SOTA 模型問題分析**  
1. **資料標註邊界模糊 (Transition 與 Failure 差異小)**  
   - LSTM 模型難以捕獲短期微妙信號變化  
   - Attention-based 模型易放大主要特徵，忽略微小退化跡象  
2. **多維特徵雜訊干擾 (如 Fy, Fz 無用或錯誤特徵)**  
   - LSTM 等序列模型無法自動忽略低質特徵 (如 Fy 感測器異常)  
3. **模型過深且數據不足 (如20層 CNN 導致過擬合)**  

### ✅ **1D-CNN 表現優異的原因**  
1. **局部特徵學習能力強**：CNN 擅長短期微小特徵學習 (如力訊號輕微變化)  
2. **特徵選擇自動性高**：1D-CNN 可自動聚焦有用特徵 (如 Fx)，無需人工特徵工程  
3. **輕量架構具泛化能力**：僅 3~5 層 CNN 已具備良好效果，且小數據下不易過擬合  

---

## 🎯 9️⃣ 研究亮點與貢獻  
✅ **雙重效用 (Dual Utility)**：同時實現 **刀具健康監測** 與 **實驗優化**  
✅ **無需特徵工程 (No Feature Engineering)**：直接從原始訊號學習特徵  
✅ **輕量即時性 (Lightweight & Real-Time)**：3層 1D-CNN 結構簡單，具備即時應用潛力  
✅ **數據異常診斷 (Data Anomaly Detection)**：模型自動揭示 Fy 感測器可能異常  
✅ **通用性強 (Generalization)**：無需針對個別刀具調整，即可維持高效能  

---

## 💡 🔮 10️⃣ 結論與未來展望  
### ✅ **研究結論**  
- 使用輕量級 **1D-CNN** 成功實現 **刀具壽命預測**，效能 **優於多種先進模型 (SOTA)**。  
- 分析證實 **採樣率可從 2000Hz 降至 50Hz** 而不損準確度，具備 **資源優化潛力**。  
- 模型能自動檢測 **感測器異常 (如 Fy 數據異常)**，提供即時反饋以優化實驗。  

### 🚀 **未來研究方向**  
1. **多模態數據整合**：如加入 **振動訊號、熱成像、視覺數據** 提升模型表現。  
2. **模型改進**：探索 **1D-CNN + Attention** 混合模型，提升長期序列學習能力。  
3. **資料標註優化**：如 **過渡期 (Transition)** 區間標註細化，減少模型混淆。  

---
