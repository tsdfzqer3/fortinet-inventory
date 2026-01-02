# 🏢 Fortinet 產品庫存監控系統

多人協作雲端版 - 使用 Google Sheets 同步資料

## 🌟 功能特色

- ✅ 即時庫存監控（自動同步廠商庫存）
- ✅ 料件管理（支援 Excel 批次匯入）
- ✅ 採購訂單追蹤
- ✅ 型號庫存共享計算（同系列產品共用庫存）
- ✅ 雲端資料同步（多人共用）
- ✅ 低庫存預警
- ✅ 資料匯出功能

## 📊 系統架構

```
前端介面 (GitHub Pages)
    ↓
本地暫存 (localStorage)
    ↓
雲端資料源 (Google Sheets)
    ├── 廠商庫存（自動同步）
    ├── 料件清單（手動同步）
    └── 訂單記錄（手動同步）
```

## 🚀 使用方式

### 線上版本
訪問：`https://您的帳號.github.io/fortinet-inventory/`

### 本地使用
下載 `index.html` 用瀏覽器開啟即可

## 📖 詳細說明

請參閱 [GitHub Pages 部署指南](./GitHub-Pages-部署指南.md)

## 🔧 技術細節

- 純前端應用（HTML + JavaScript）
- 使用 Tailwind CSS 樣式框架
- 使用 SheetJS 處理 Excel 檔案
- 資料儲存：localStorage + Google Sheets

## 📝 更新記錄

- 2025/01/02: 初始版本，支援雲端同步
- 支援型號庫存共享計算
- 自動忽略重複料號
- 新增資料匯出功能

## 📄 授權

內部使用專案
