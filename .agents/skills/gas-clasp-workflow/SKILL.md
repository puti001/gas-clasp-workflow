---
name: gas-clasp-workflow
description: Google Apps Script (GAS) 本地開發與自動同步 (clasp) 工作流。支援 clasp v3、自動部署、防坑網址解析與隱私防護。
---

# GAS Clasp 開發與自動同步工作流

本技能提供 Google Apps Script (GAS) 本地開發與自動同步 (clasp) 的標準化指令、最新 clasp v3 命令對照、以及開發防坑指南。

## 觸發情境
當提到以下內容時載入本技能：
- 「GAS」、「Google Apps Script」、「clasp」
- 「推送」、「部署到 GAS」、「更新 GAS 程式碼」、「push」
- 「下載 GAS 程式碼」、「從雲端拉取」、「pull」

## 核心開發原則

### 1. clasp v3 指令對照（重要！）
clasp v3 對許多指令進行了重命名。請一律使用 v3 的新指令以避免執行錯誤：

| 舊指令（v2，已廢棄） | 新指令（v3） | 用途 |
|---|---|---|
| `clasp create` | `clasp create-script` | 建立專案 |
| `clasp clone` | `clasp clone-script` | 連結並下載專案 |
| `clasp open` | `clasp open-script` | 開啟 GAS 瀏覽器編輯器 |
| `clasp deploy` | `clasp create-deployment` | 建立部署 |
| `clasp deployments` | `clasp list-deployments` | 列出部署列表 |
| `clasp undeploy` | `clasp delete-deployment` | 刪除部署 |
| `clasp status` | `clasp show-file-status` | 查看本地與雲端檔案狀態 |
| `clasp login --status` | `clasp show-authorized-user` | 檢查目前登入的使用者帳號 |
| （無） | `clasp open-container` | 開啟綁定的容器（如試算表） |
| （無） | `clasp open-web-app` | 開啟部署好的網頁應用程式 |

### 2. 🔴 嚴禁自己拼湊網頁應用程式網址
- **症狀**：拿 `.clasp.json` 裡的 `scriptId` 去拼湊 `https://script.google.com/macros/s/<scriptId>/exec`，會導致網頁開啟出現 `404 網頁不存在`。
- **正確做法**：一律先執行部署，然後從 API 獲取真實網址：
  ```powershell
  npx @google/clasp create-deployment --description "版本名稱"
  ```
  取得 **deploymentId** 後，執行：
  ```powershell
  npx @google/clasp open-web-app <deploymentId> --json
  ```
  帶入 `--json` 旗標，它會印出 `{"url": "真正的網址"}`。**一律使用它所輸出的網址**，不准自己拼寫。

### 3. 本地與雲端檔案對應
- **後端程式碼**：本地寫為 `.js` 檔（如 `code.js`），執行 `clasp push` 後會自動轉換成雲端的 `.gs` 檔（如 `code.gs`）。
- **前端程式碼**：本地寫為 `.html` 檔（如 `index.html`），保持不變。
- 專案程式碼一律在本地端完成修改，並執行：
  ```powershell
  npx @google/clasp push
  ```

### 4. 受管理帳號限制與登入
- 學校/公司 Workspace 帳號常會遇到 `admin_policy_enforced` 限制。如果遇到，主動引導使用者登出並使用**個人 Gmail 帳號**登入。
- 執行 `clasp login` 前，先向使用者說明瀏覽器會開啟並需要進行個人帳號授權。

### 5. 退場機制（不無限重試）
- 如果 clasp 在登入或 API 授權階段連續失敗兩次，不要一直重試。主動向使用者提出退路：**「clasp 自動同步被卡住了。我們改為手動貼代碼方式，我把程式碼提供給你，你手動貼到 script.google.com 編輯器上即可。」** 保證專案能繼續完成最重要。

### 6. 隱私紅線
- 在發布 Web App 時，**嚴禁將使用者或學生的真實姓名、身分證字號、電話、聯絡方式等個人隱私資訊寫進雲端試算表或代碼中**。如果使用者提供的測試資料中有敏感資訊，請主動指出並建議移除或使用流水號代碼代替。
