# Fortinet 庫存監控系統 - GitHub Pages 部署指南

## 📋 部署步驟

### 第一步：註冊 GitHub 帳號（如果還沒有）

1. 前往 https://github.com
2. 點擊右上角「Sign up」
3. 填寫資料完成註冊（免費）

### 第二步：建立新的 Repository（儲存庫）

1. 登入 GitHub 後，點擊右上角的「+」→ 「New repository」
2. 填寫資料：
   - Repository name: `fortinet-inventory` （或您喜歡的名稱）
   - Description: `Fortinet 產品庫存監控系統`
   - 選擇 **Public**（公開，才能使用免費的 GitHub Pages）
   - ✅ 勾選「Add a README file」
3. 點擊「Create repository」

### 第三步：上傳檔案

1. 在您剛建立的 repository 頁面，點擊「Add file」→「Upload files」
2. 把 `index.html` 檔案拖曳到頁面上（或點擊選擇檔案）
3. 在下方填寫 Commit message：`Initial commit - 上傳庫存監控系統`
4. 點擊「Commit changes」

### 第四步：啟用 GitHub Pages

1. 在 repository 頁面，點擊「Settings」（設定）
2. 在左側選單找到「Pages」
3. 在「Branch」區域：
   - 選擇 **main**（或 master）
   - 資料夾選擇 **/ (root)**
   - 點擊「Save」
4. 等待 1-2 分鐘，頁面會顯示：
   ```
   Your site is live at https://您的帳號.github.io/fortinet-inventory/
   ```

### 第五步：設定雲端網址

1. 先建立 Google Sheets（如前面說明）
2. 發布兩個分頁為 CSV，取得網址
3. 回到 GitHub，點擊 `index.html` 檔案
4. 點擊右上角的「編輯」圖示（鉛筆）
5. 找到這段程式碼：
   ```javascript
   const CLOUD_CONFIG = {
       supplierStock: '...',
       productCatalog: '', // ← 填入料件清單 CSV 網址
       orderHistory: ''    // ← 填入訂單記錄 CSV 網址
   };
   ```
6. 填入您的 Google Sheets CSV 網址
7. 點擊「Commit changes」

### 第六步：分享給同事

✅ 完成！現在您可以把網址分享給同事：
```
https://您的帳號.github.io/fortinet-inventory/
```

所有人用這個網址就能存取系統！

---

## 🔄 如何更新網站

當您修改 HTML 檔案後：

1. 進入 GitHub repository
2. 點擊 `index.html`
3. 點擊編輯圖示（鉛筆）
4. 修改內容
5. 點擊「Commit changes」
6. 等待 1-2 分鐘，網站就會自動更新

---

## 📱 使用注意事項

### 資料同步方式：

1. **料件清單和訂單記錄：**
   - 匯入 Excel → 點「匯出 CSV」
   - 把 CSV 內容複製到 Google Sheets
   - 點「☁️ 從雲端同步」載入最新資料

2. **廠商庫存：**
   - 自動從您原本的 Google Sheets 載入
   - 每次開啟網站都會自動同步

3. **多人協作：**
   - 所有人用同一個網址
   - 點「從雲端同步」就能看到最新資料
   - 本地也會有備份（離線也能查看）

---

## 🔒 安全性說明

- ✅ 網址是公開的（任何人都能存取）
- ⚠️ 如果資料機密，建議：
  - 不要在 Google Sheets 放敏感資料
  - 或使用 Private repository（需付費 GitHub Pro）
  - 或設定 Google Sheets 存取權限

---

## 💡 進階功能（選用）

### 自訂網域名稱

如果您有自己的網域（如 inventory.yourcompany.com），可以：

1. 在 GitHub Pages 設定中點擊「Custom domain」
2. 輸入您的網域名稱
3. 在網域商設定 DNS 記錄（指向 GitHub）

詳細步驟：https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

---

## ❓ 常見問題

**Q: 網站更新後要多久才會生效？**
A: 通常 1-2 分鐘，最多 10 分鐘。

**Q: 可以設定密碼保護嗎？**
A: GitHub Pages 免費版不支援。如需密碼保護，建議升級到付費方案或使用其他平台。

**Q: 資料會不會被別人看到？**
A: 如果 repository 是 Public，HTML 檔案是公開的。但實際資料在 Google Sheets，可以設定存取權限。

**Q: 可以改回 localhost 嗎？**
A: 可以！隨時可以下載 HTML 檔案到本地使用。

---

## 📞 需要幫助？

如有問題，可以：
1. 查看 GitHub Pages 官方文件：https://pages.github.com/
2. 或聯繫我協助除錯
