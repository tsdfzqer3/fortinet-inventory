# 🎯 多類別庫存系統 v2.0 使用說明

> 版本：2.0.20260114.001

---

## 🚀 系統已就緒

✅ **所有功能已完成！**
- 三個類別切換按鈕
- 獨立資料管理
- Firebase 即時同步
- 完整的匯入/匯出功能

⏳ **待補充資料**：
- Server 硬體的 Google Sheets CSV 網址
- Client 硬體的 Google Sheets CSV 網址
- Server 和 Client 的料件清單（使用時再匯入）

---

## 📋 三大類別

### 1. 🌐 網通產品
- **狀態**：✅ 已設定完成
- **包含**：Fortinet 相關產品
- **資料來源**：已設定
- **可以使用**：立即可用

### 2. 🖥️ Server 硬體
- **狀態**：⏳ 待補充資料
- **包含**：伺服器、存儲設備
- **資料來源**：待設定 CSV 網址
- **需要準備**：
  - Google Sheets CSV 網址
  - 料件清單 Excel

### 3. 💻 Client 硬體
- **狀態**：⏳ 待補充資料
- **包含**：PC、NB、顯示器等
- **資料來源**：待設定 CSV 網址
- **需要準備**：
  - Google Sheets CSV 網址
  - 料件清單 Excel

---

## 🎮 如何使用

### 切換類別

在頁面上方會看到三個大按鈕：

```
┌─────────────┬─────────────┬─────────────┐
│  🌐 網通產品  │ 🖥️ Server  │ 💻 Client  │
│   (藍色)     │             │             │
└─────────────┴─────────────┴─────────────┘
```

- **藍色按鈕**：目前選擇的類別
- **白色按鈕**：點擊可切換到該類別

### 每個類別獨立管理

切換類別後，系統會顯示該類別的：
- ✅ 料件清單
- ✅ 廠商庫存
- ✅ 採購訂單
- ✅ 統計數字

---

## 📊 目前可用功能

### 網通產品（Fortinet）
✅ 完全可用
- 查看庫存
- 匯入訂單
- 搜尋產品
- 訂單管理

### Server 硬體
🔧 部分可用
- ✅ 切換到此類別
- ✅ 匯入料件清單 Excel
- ✅ 匯入採購訂單 Excel
- ⏳ 廠商庫存（需要 CSV 網址）

**使用方式**：
1. 點擊「🖥️ Server 硬體」切換類別
2. 點擊「📂 匯入料件Excel」
3. 選擇 Server 料件清單檔案
4. 等廠商庫存 CSV 設定後，會自動載入庫存

### Client 硬體
🔧 部分可用
- ✅ 切換到此類別
- ✅ 匯入料件清單 Excel
- ✅ 匯入採購訂單 Excel
- ⏳ 廠商庫存（需要 CSV 網址）

**使用方式**：
1. 點擊「💻 Client 硬體」切換類別
2. 點擊「📂 匯入料件Excel」
3. 選擇 Client 料件清單檔案
4. 等廠商庫存 CSV 設定後，會自動載入庫存

---

## 🔧 後續設定（當資料準備好時）

### 步驟 1：準備 Google Sheets

#### Server 硬體庫存表

| A 欄 | B 欄 | C 欄 | D 欄 | F 欄 |
|------|------|------|------|------|
| 型號 | 品名 | 型號 | 庫存 | 更新日期 |
| R740 | Dell PowerEdge R740 | R740 | 25 | 2026/1/14 |
| DL380 | HPE ProLiant DL380 | DL380 | 15 | 2026/1/14 |

**發佈步驟**：
1. 檔案 → 共用 → 發佈至網路
2. 選擇「逗號分隔值 (.csv)」
3. 複製網址

#### Client 硬體庫存表

格式同上，但填入 PC、NB 等資料。

### 步驟 2：提供 CSV 網址

把兩個 CSV 網址提供給我：
```
Server CSV: https://docs.google.com/spreadsheets/d/e/2PACX-xxx/pub?output=csv
Client CSV: https://docs.google.com/spreadsheets/d/e/2PACX-xxx/pub?output=csv
```

### 步驟 3：我會更新程式碼

我會在 5 分鐘內：
1. 更新 index.html
2. 設定兩個 CSV 網址
3. 測試自動載入功能
4. 提供新版本給您

### 步驟 4：使用完整功能

更新後，系統會自動：
- ✅ 切換到 Server 類別 → 自動載入 Server 庫存
- ✅ 切換到 Client 類別 → 自動載入 Client 庫存
- ✅ 計算剩餘庫存
- ✅ 顯示低庫存警告

---

## 💡 現在可以做什麼？

### 立即可以使用

#### 1. 網通產品（Fortinet）
完全正常運作，所有功能都可用。

#### 2. Server 硬體（先匯入料件）
```
步驟：
1. 準備 Server 料件清單 Excel
   A 欄：料號（例如：SERVER-001）
   B 欄：品名
   C 欄：型號

2. 點擊「🖥️ Server 硬體」

3. 點擊「📂 匯入料件Excel」

4. 選擇檔案，匯入成功！

5. 此時可以看到料件清單，但庫存顯示「-」
   （等 CSV 設定後會自動載入庫存）
```

#### 3. Client 硬體（先匯入料件）
步驟同上，準備 Client 料件清單匯入。

---

## 📁 資料存儲說明

### 每個類別獨立存儲

**LocalStorage**：
```
forti-product-catalog-network   # 網通產品料件
forti-product-catalog-server    # Server 料件
forti-product-catalog-client    # Client 料件
```

**Firebase**：
```
/network/productCatalog/   # 網通產品
/network/orderHistory/

/server/productCatalog/    # Server 硬體
/server/orderHistory/

/client/productCatalog/    # Client 硬體
/client/orderHistory/
```

### 資料不會互相干擾

- ✅ 切換類別時，資料自動切換
- ✅ 每個類別的訂單獨立計算
- ✅ 不會搞混不同類別的產品

---

## 🎯 建議的使用流程

### 第一階段：先用網通產品（現在）
1. 繼續使用網通產品（Fortinet）
2. 熟悉系統操作
3. 確認所有功能正常

### 第二階段：準備 Server 資料（1-2 天）
1. 建立 Server 料件清單 Excel
2. 建立 Server Google Sheets 庫存表
3. 發佈 CSV，取得網址
4. 提供給我設定

### 第三階段：準備 Client 資料（1-2 天）
1. 建立 Client 料件清單 Excel
2. 建立 Client Google Sheets 庫存表
3. 發佈 CSV，取得網址
4. 提供給我設定

### 第四階段：完整啟用（設定完成後）
1. Server 和 Client 都能自動載入庫存
2. 三個類別都完全可用
3. 同事可以切換查看不同類別

---

## 📞 需要設定時請提供

當您準備好資料時，請提供：

**Server 硬體**：
```
CSV 網址：https://docs.google.com/...
料件清單：（上傳 Excel 檔案）
```

**Client 硬體**：
```
CSV 網址：https://docs.google.com/...
料件清單：（上傳 Excel 檔案）
```

我會在 5 分鐘內完成設定！

---

## 🎉 系統優勢

### 多類別管理
- ✅ 一個系統管理三種產品
- ✅ 資料獨立，不會混淆
- ✅ 切換方便，一鍵切換

### 團隊協作
- ✅ Firebase 即時同步
- ✅ 多人可同時使用
- ✅ 資料即時更新

### 擴展性強
- ✅ 未來可以再加新類別
- ✅ 每個類別獨立設定
- ✅ 不影響現有功能

---

## 📋 Excel 範本

### Server 料件清單範本

| A (料號) | B (品名) | C (型號) |
|---------|---------|---------|
| SERVER-001 | Dell PowerEdge R740 雙處理器伺服器 | R740 |
| SERVER-002 | HPE ProLiant DL380 Gen10 伺服器 | DL380 |
| STORAGE-001 | NetApp DS4246 儲存櫃 | DS4246 |
| STORAGE-002 | QNAP TS-873AU-RP NAS 儲存設備 | TS-873AU |

### Client 料件清單範本

| A (料號) | B (品名) | C (型號) |
|---------|---------|---------|
| PC-001 | Lenovo ThinkCentre M70s 商用電腦 | M70s |
| PC-002 | Dell OptiPlex 7090 SFF 電腦 | 7090 |
| NB-001 | Lenovo ThinkPad X1 Carbon Gen9 | X1C9 |
| NB-002 | Dell Latitude 7420 商用筆電 | 7420 |
| MONITOR-001 | Dell U2723DE 27吋 4K 顯示器 | U2723DE |
| MONITOR-002 | BenQ PD2705U 27吋專業顯示器 | PD2705U |

---

## ✅ 系統已就緒！

**目前狀態**：
- 🌐 網通產品：✅ 完全可用
- 🖥️ Server 硬體：🔧 可匯入料件，等 CSV 設定
- 💻 Client 硬體：🔧 可匯入料件，等 CSV 設定

**現在可以**：
1. 繼續使用網通產品類別
2. 先匯入 Server 和 Client 的料件清單
3. 準備廠商庫存 Google Sheets
4. 等資料準備好再設定 CSV

**系統完全可用，隨時開始！** 🚀
