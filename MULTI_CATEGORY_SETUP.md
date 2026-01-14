# 🎯 多類別庫存系統 - 設定指南

> 版本 2.0.20260114.001 - 支援三大類別切換

---

## 📋 系統架構說明

### 三大類別

1. **🌐 網通產品**（已設定）
   - Fortinet 相關產品
   - 資料來源：已設定完成

2. **🖥️ Server 硬體**（待設定）
   - 伺服器設備
   - 存儲設備
   - 資料來源：需要您提供

3. **💻 Client 硬體**（待設定）
   - PC 電腦
   - NB 筆電
   - 顯示器
   - 其他個人電腦設備
   - 資料來源：需要您提供

---

## 🔧 系統特點

### 獨立管理
- ✅ 每個類別有獨立的料件清單
- ✅ 每個類別有獨立的廠商庫存來源
- ✅ 每個類別有獨立的訂單記錄
- ✅ 每個類別有獨立的 Firebase 儲存路徑

### 切換功能
- 點選類別按鈕即可切換
- 當前類別會以藍色高亮顯示
- 顯示當前類別的料件數量

---

## 📊 需要提供的資料

### Server 硬體類別

#### 1. 料件清單 Excel

| 欄位 | 說明 | 範例 |
|------|------|------|
| A 欄 | 料號 | SERVER-001, STORAGE-001 |
| B 欄 | 品名 | Dell PowerEdge R740 雙處理器伺服器 |
| C 欄 | 型號 | R740, DS4246 |

**範例**：
```
A             B                                    C
料號           品名                                  型號
SERVER-001    Dell PowerEdge R740 伺服器            R740
SERVER-002    HPE ProLiant DL380 Gen10             DL380
STORAGE-001   NetApp DS4246 儲存櫃                  DS4246
STORAGE-002   QNAP TS-873AU-RP NAS                 TS-873AU
```

#### 2. 廠商庫存 Google Sheets

**格式要求**：
- A 欄：型號（例如：R740）
- B 欄：品名
- C 欄：型號（重複，用於對應）
- D 欄：庫存數量
- F 欄：更新日期（格式：2026/1/14 或 更新日期:2026/1/14）

**發佈步驟**：
1. 建立 Google Sheets
2. 檔案 → 共用 → 發佈至網路
3. 選擇「逗號分隔值 (.csv)」格式
4. 複製 CSV 網址
5. 提供給我設定

#### 3. 採購訂單 Excel（選用）

| 欄位 | 說明 | 範例 |
|------|------|------|
| B 欄 | 下單日期 | 2026/01/14 |
| I 欄 | 採購單號 | PO-SERVER-001 |
| J 欄 | 料號 | SERVER-001 |
| L 欄 | 數量 | 2 |
| P 欄 | 訂單單號 | SO-SERVER-001 |

---

### Client 硬體類別

#### 1. 料件清單 Excel

| 欄位 | 說明 | 範例 |
|------|------|------|
| A 欄 | 料號 | PC-001, NB-001, MONITOR-001 |
| B 欄 | 品名 | Lenovo ThinkCentre M70s 商用電腦 |
| C 欄 | 型號 | M70s, X1C9, U2723DE |

**範例**：
```
A             B                                    C
料號           品名                                  型號
PC-001        Lenovo ThinkCentre M70s 商用電腦      M70s
PC-002        Dell OptiPlex 7090 SFF               7090
NB-001        Lenovo ThinkPad X1 Carbon Gen9       X1C9
NB-002        Dell Latitude 7420                   7420
MONITOR-001   Dell U2723DE 27吋 4K 顯示器           U2723DE
MONITOR-002   BenQ PD2705U 27吋 4K                 PD2705U
```

#### 2. 廠商庫存 Google Sheets

格式同上，需要：
- 建立新的 Google Sheets
- 發佈為 CSV
- 提供 CSV 網址

#### 3. 採購訂單 Excel（選用）

格式同上。

---

## 🔨 設定步驟

### 步驟 1：提供資料

**請準備以下資料給我**：

**Server 硬體**：
- [ ] 料件清單 Excel 檔案
- [ ] 廠商庫存 Google Sheets CSV 網址
- [ ] 採購訂單 Excel（如有）

**Client 硬體**：
- [ ] 料件清單 Excel 檔案
- [ ] 廠商庫存 Google Sheets CSV 網址
- [ ] 採購訂單 Excel（如有）

### 步驟 2：我會幫您設定

收到資料後，我會：
1. ✅ 更新 `index.html` 中的 CSV 網址
2. ✅ 測試資料載入
3. ✅ 提供更新後的檔案

### 步驟 3：匯入料件清單

您需要：
1. 開啟更新後的系統
2. 切換到對應類別（例如：Server 硬體）
3. 點選「📂 匯入料件Excel」
4. 選擇該類別的料件清單檔案
5. 等待匯入完成

### 步驟 4：自動載入庫存

系統會自動：
- ✅ 載入該類別的廠商庫存
- ✅ 顯示庫存數量
- ✅ 計算剩餘庫存

### 步驟 5：匯入訂單（選用）

如有採購訂單：
1. 切換到對應類別
2. 點選「📊 上傳採購訂單」
3. 選擇該類別的訂單檔案
4. 系統會自動計算已下單數量

---

## 📁 資料存儲架構

### Firebase 路徑

```
Firebase Realtime Database
├── network/                    # 網通產品
│   ├── productCatalog/        # 料件清單
│   └── orderHistory/          # 訂單記錄
├── server/                     # Server 硬體
│   ├── productCatalog/        # 料件清單
│   └── orderHistory/          # 訂單記錄
└── client/                     # Client 硬體
    ├── productCatalog/        # 料件清單
    └── orderHistory/          # 訂單記錄
```

### LocalStorage 鍵值

```
forti-product-catalog-network   # 網通產品料件
forti-product-catalog-server    # Server 料件
forti-product-catalog-client    # Client 料件

forti-supplier-stock-network    # 網通產品庫存
forti-supplier-stock-server     # Server 庫存
forti-supplier-stock-client     # Client 庫存

forti-order-history-network     # 網通產品訂單
forti-order-history-server      # Server 訂單
forti-order-history-client      # Client 訂單
```

---

## 🎨 UI 變更說明

### 舊版（v1.5）
```
┌─────────────────────────────────────┐
│ 公司料件數 │ 無庫存 │ 低庫存 │ 訂單數 │
└─────────────────────────────────────┘
```

### 新版（v2.0）
```
┌───────────────────────────────────────────┐
│ 🌐 網通產品 │ 🖥️ Server │ 💻 Client │
│   (已選取)   │            │            │
└───────────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 料件總數 │ 無庫存 │ 低庫存 │ 訂單數 │
│  (當前類別的統計)                    │
└─────────────────────────────────────┘
```

---

## 🔍 程式碼位置

### 類別設定（第 103-131 行）

```javascript
const CATEGORIES = {
    network: {
        id: 'network',
        name: '網通產品',
        icon: '🌐',
        csvUrl: 'https://...已設定...',
        firebasePath: 'network'
    },
    server: {
        id: 'server',
        name: 'Server 硬體',
        icon: '🖥️',
        csvUrl: '',  // ← 需要設定
        firebasePath: 'server'
    },
    client: {
        id: 'client',
        name: 'Client 硬體',
        icon: '💻',
        csvUrl: '',  // ← 需要設定
        firebasePath: 'client'
    }
};
```

### 我需要您提供

**Server 硬體**：
- Google Sheets CSV 網址（類似這樣）：
  ```
  https://docs.google.com/spreadsheets/d/e/2PACX-xxx/pub?output=csv
  ```

**Client 硬體**：
- Google Sheets CSV 網址（類似這樣）：
  ```
  https://docs.google.com/spreadsheets/d/e/2PACX-xxx/pub?output=csv
  ```

---

## 💡 使用建議

### 料號命名規則

建議使用統一的命名規則：

**Server 硬體**：
```
SERVER-001, SERVER-002, ...     # 伺服器
STORAGE-001, STORAGE-002, ...   # 儲存設備
SWITCH-001, SWITCH-002, ...     # 交換器（如果不放在網通）
```

**Client 硬體**：
```
PC-001, PC-002, ...             # 桌上型電腦
NB-001, NB-002, ...             # 筆記型電腦
MONITOR-001, MONITOR-002, ...   # 顯示器
KB-001, KB-002, ...             # 鍵盤
MOUSE-001, MOUSE-002, ...       # 滑鼠
```

### 型號對應

確保型號在料件清單和廠商庫存中**完全一致**：

**料件清單**：
```
型號: R740
```

**廠商庫存**：
```
型號: R740  ← 必須完全相同
```

---

## 🚀 快速開始

### 現在就開始設定！

1. **準備 Server 硬體資料**
   - [ ] 建立 Google Sheets（格式參考上面）
   - [ ] 發佈為 CSV
   - [ ] 複製 CSV 網址
   - [ ] 準備料件清單 Excel

2. **準備 Client 硬體資料**
   - [ ] 建立 Google Sheets
   - [ ] 發佈為 CSV
   - [ ] 複製 CSV 網址
   - [ ] 準備料件清單 Excel

3. **提供給我**
   - 把兩個 CSV 網址和 Excel 檔案給我
   - 我會立即幫您設定完成

---

## 📞 需要協助？

請提供以下資訊：

**Server 硬體**：
- [ ] Google Sheets CSV 網址
- [ ] 料件清單 Excel（上傳檔案）
- [ ] 採購訂單 Excel（如有）

**Client 硬體**：
- [ ] Google Sheets CSV 網址
- [ ] 料件清單 Excel（上傳檔案）
- [ ] 採購訂單 Excel（如有）

提供後，我會在 10 分鐘內完成設定！🚀

---

## 📋 檢查清單

設定完成後，請確認：

**Server 硬體**：
- [ ] 可以切換到 Server 類別
- [ ] 料件清單已匯入
- [ ] 廠商庫存自動載入
- [ ] 顯示正確的庫存數量
- [ ] 訂單可以匯入（如有）

**Client 硬體**：
- [ ] 可以切換到 Client 類別
- [ ] 料件清單已匯入
- [ ] 廠商庫存自動載入
- [ ] 顯示正確的庫存數量
- [ ] 訂單可以匯入（如有）

**多類別切換**：
- [ ] 三個類別按鈕都可以點選
- [ ] 切換時資料正確變更
- [ ] 當前類別有藍色高亮
- [ ] 每個類別的統計數字正確

完成！🎉
