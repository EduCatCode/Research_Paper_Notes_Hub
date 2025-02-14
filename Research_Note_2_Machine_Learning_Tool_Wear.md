# 📘 研究論文紀錄：2. Milling Tool Wear Estimation Using Machine Learning with Feature Extraction Approach

---

## 📝 1️⃣ 論文基本資訊  
- **標題**: Milling Tool Wear Estimation Using Machine Learning with Feature Extraction Approach  
- **作者**: Aarya Misal, Arunkumar Bongale, Hrishikesh Karandikar, Satish Kumar, Sameer Sayyad, Vivek Warke  
- **所屬機構**: Symbiosis Institute of Technology, Pune, India  
- **會議名稱**: 2024 MIT Art, Design and Technology School of Computing International Conference (MITADTSoCiCon)  
- **發表日期**: 2024年4月25日 - 27日  
- **出版機構**: IEEE Xplore  
- **DOI**: 10.1109/MITADTSoCiCon60330.2024.10575626  

---

## 💡 2️⃣ 研究背景與動機  
### 📌 **背景問題**
- 在 CNC 銑削中，刀具磨耗會導致加工精度下降、工件表面粗糙度變差，甚至造成機器損壞。因此，**刀具磨耗預測 (Tool Wear Prediction)** 是維持高效製造和進行 **預測性維護 (Predictive Maintenance)** 的關鍵。  

### 📌 **現有問題 (Research Gap)**：
1. 現有模型 **準確度依賴特定切削條件**，在大幅波動的切削情況下表現不佳。  
2. 大多數技術依賴 **固定結構的神經網絡**，訓練成本高，且難以保證在多變切削條件下的準確度。  

### 🚀 **研究目標**  
- 提出基於 **機器學習 (Machine Learning, ML)** 與 **特徵工程 (Feature Engineering)** 方法的 **刀具磨耗預測模型**，提升多元切削條件下的預測準確度，並協助達成 **預測性維護 (Predictive Maintenance)**。  

---

## 🧩 3️⃣ 研究貢獻  
### ✅ **多感測器數據實驗**  
- 使用 **NUAA Ideahouse Dataset** 進行實驗 (包含切削力、加速度、電流、振動與對應刀具磨耗值)。  

### ✅ **特徵工程與選擇**  
- 使用 **TSFEL (Time Series Feature Extraction Library)** 進行自動化特徵提取：  
  - **時間域 (Temporal)**  
  - **頻譜域 (Spectral)**  
  - **統計域 (Statistical)**  
- 採用 **PCC (Pearson's Correlation Coefficient)** 進行特徵篩選，選出最具影響力的特徵。  

### ✅ **多模型效能比較**  
- 建立多個機器學習模型進行效能比較：  
  - **K-Nearest Neighbors (KNN)**  
  - **Decision Tree (DT)**  
  - **Random Forest (RF)**  

### ✅ **多評估指標分析**  
- 使用多種模型效能評估指標：  
  - **R² Score (判定係數)**  
  - **MSE (均方誤差)**  
  - **MAPE (平均絕對百分比誤差)**  

---

## 📊 4️⃣ 實驗數據集與感測器配置  
### 📌 **數據來源與實驗設計**  
- **數據集**: NUAA Ideahouse 刀具磨耗資料集  
- **加工中心**: DMU™ 80P duoBLOCK CNC 加工中心  
- **刀具**: 硬質合金 (Solid Carbide)  
- **工件材質**: TC4 鈦合金  
- **切削參數**:
  - 進給速率 (Feed Rate): 0.045 mm/r  
  - 主軸轉速 (Spindle Speed): 1750 r/min  
- **實驗設計**: 進行 30 次直角正交切削實驗，每次記錄對應刀具磨耗值。  

### 📌 **感測器配置**  
- **動力計 (Dynamometer)**: 測量切削力 (Fx, Fy, Fz)  
- **加速規 (Accelerometer)**: 測量刀具振動訊號 (X, Y, Z 三軸)  
- **電流感測器 (Current Sensor)**: 測量主軸電流變化 (反映切削負荷)  
- **振動感測器 (Vibration Sensor)**: 測量切削過程中的振動頻率與幅值  

---

## 🧵 5️⃣ 方法論 (Methodology)  

### 📌 Step 1: 資料預處理 (Data Preprocessing)  
- **資料清理 (Data Cleaning)**：移除缺失值 (Null Values) 與異常值 (Outliers)。  
- **資料標準化 (Feature Scaling)**：  
  - 使用 **MinMax Scaler**：將資料縮放至 0 到 1 區間。  
  - 使用 **Standard Scaler**：將資料轉換為均值 0、標準差 1 的常態分佈。  

### 📌 Step 2: 特徵提取 (Feature Extraction) - 使用 TSFEL  
- 使用 **TSFEL (Time Series Feature Extraction Library)** 從時間序列資料中自動提取多維度特徵：  
  - **時間域 (Temporal Features)**：18項特徵 (如：平均值 (Mean)、標準差 (Std)、斜度 (Slope)、零交率 (Zero Crossing Rate) 等)  
  - **頻譜域 (Spectral Features)**：27項特徵 (如：頻譜熵 (Spectral Entropy)、峰值頻率 (Peak Frequency)、頻譜重心 (Spectral Centroid) 等)  
  - **統計域 (Statistical Features)**：16項特徵 (如：均方根 (RMS)、形狀因子 (Shape Factor)、變異數 (Variance) 等)  

### 📌 Step 3: 特徵選擇 (Feature Selection) - 使用 PCC  
- 使用 **PCC (Pearson's Correlation Coefficient)** 進行特徵篩選，挑選與刀具磨耗高度相關的特徵：  
  - **時間域 (Temporal)**：選出 10 個關鍵特徵  
  - **頻譜域 (Spectral)**：選出 16 個關鍵特徵  
  - **統計域 (Statistical)**：選出 16 個關鍵特徵  
- **PCC 選擇原因**：簡單、高效，能量化線性相關性，有助於減少模型計算成本並防止過擬合 (Overfitting)。  

### 💻 Step 4: 機器學習模型建立 (ML Model Training)  
- 測試多種模型效能，並使用三種資料組合：  
  1. **全特徵 (All Features)**  
  2. **PCC 選定特徵 (Selected Features)**  
  3. **PCC 選定並標準化特徵 (Scaled Selected Features)**  

- 測試的模型包含：  
  - **K-Nearest Neighbors (KNN)**  
  - **Decision Tree (DT)**  
  - **Random Forest (RF)**  

### 📈 Step 5: 模型效能評估 (Model Evaluation)  
- 使用多種評估指標衡量模型效能：  
  - **R² Score (判定係數)**：評估模型解釋變異數的能力，1.0為完美擬合。  
  - **MSE (均方誤差, Mean Squared Error)**：數值越小代表模型預測誤差越低。  
  - **MAPE (平均絕對百分比誤差, Mean Absolute Percentage Error)**：衡量模型預測偏差的百分比。  

---

## 🧪 6️⃣ 實驗結果與分析 (Results and Discussions)  

### 📊 1️⃣ **時間域 (Temporal Features) 結果分析**  
| **模型** | **資料組合** | **MSE** | **MAPE** | **R² Score** |
|----------|--------------|--------|---------|------------|
| **KNN** | 全特徵 | 0.0012 | 0.19 | 0.11 |
| **KNN** | 選定特徵 | 0.0011 | 0.17 | 0.21 |
| **KNN** | 標準化選定特徵 | 0.0007 | 0.12 | 0.52 |
| **Decision Tree** | 全特徵 | 0.0009 | 0.16 | 0.37 |
| **Random Forest** | 全特徵 | 0.0004 | 0.09 | **0.72 (最佳)** |

✅ **分析結論**：  
- 在 **時間域 (Temporal)** 特徵中，**Random Forest (RF)** 表現最佳，R² 達 **0.72**。  
- **KNN** 表現受限，即使經過特徵選擇與標準化，效果也不如 **RF**。  

---

### 📊 2️⃣ **頻譜域 (Spectral Features) 結果分析**  
| **模型** | **資料組合** | **MSE** | **MAPE** | **R² Score** |
|----------|--------------|--------|---------|------------|
| **KNN** | 全特徵 | 0.0012 | 0.18 | 0.14 |
| **Decision Tree** | 全特徵 | 1.04e-8 | 1.9e-5 | **0.99 (最佳)** |
| **Random Forest** | 全特徵 | 2.37e-8 | 0.0001 | **0.99 (最佳)** |

✅ **分析結論**：  
- 在 **頻譜域 (Spectral)** 特徵中，**Decision Tree (DT)** 與 **Random Forest (RF)** 同樣表現出色，R² 高達 **0.99**。  
- **KNN** 在此域表現最差。  

---

### 📊 3️⃣ **統計域 (Statistical Features) 結果分析**  
| **模型** | **資料組合** | **MSE** | **MAPE** | **R² Score** |
|----------|--------------|--------|---------|------------|
| **KNN** | 全特徵 | 0.0012 | 0.18 | 0.14 |
| **Decision Tree** | 全特徵 | 6.17e-32 | 1.19e-15 | **1.0 (完美)** |
| **Random Forest** | 全特徵 | 1.1e-8 | 7.82e-5 | **0.99** |

✅ **分析結論**：  
- 在 **統計域 (Statistical)** 特徵中，**Decision Tree (DT)** 達到 **R² = 1.0 (完美擬合)**。  
- **Random Forest (RF)** 也取得 **0.99** 高分。  
- **統計域特徵** 是本研究中 **最有效的特徵維度**。  

---

## 🏷️ 7️⃣ 實驗總結與洞察  

### ✅ **特徵域影響顯著**：  
- **統計域特徵** 最具預測力，其次為 **頻譜域**，最後為 **時間域**。  

### ✅ **模型選擇影響大**：  
- **Decision Tree (DT)** 在 **統計域** 特徵下表現最完美 (**R² = 1.0**)  
- **Random Forest (RF)** 對資料量需求高，卻在多域下均表現出色 (**0.72 ~ 0.99**)  

### ✅ **特徵篩選與標準化的影響**：  
- **KNN** 對資料 **標準化 (Scaling)** 非常敏感，在縮減特徵後效果反而提升。  
- **Decision Tree (DT) 與 Random Forest (RF)** 對特徵數量不敏感，**全特徵表現更好**。  

---

## 💡 8️⃣ 研究結論與未來展望  

### ✅ **研究結論**：  
- 本研究提出基於 **TSFEL + PCC + 多模型比較** 的刀具磨耗預測框架，並驗證 **多域特徵對預測準確度的影響**。  
- **Decision Tree (DT)** 在 **統計域** 特徵中達到 **完美表現 (R² = 1.0)**，適合應用於即時監測場景。  
- **Random Forest (RF)** 效能在 **多域下均優異**，適合用於高資料量場景。  

### 🚀 **未來研究方向 (Future Work)**：  
1. **多模態數據融合 (Multi-modal Fusion)**：整合 **影像 (Machine Vision)** 或 **聲學訊號 (Acoustic Emission)**，提升模型準確度。  
2. **邊緣計算 (Edge Computing)**：引入 **Edge-Fog-Cloud 多層架構**，實現即時預測與維護建議 (工業 4.0 應用)。  
3. **強化式學習 (Reinforcement Learning)**：讓模型從長期維護歷史中持續學習與優化預測策略。  

---
