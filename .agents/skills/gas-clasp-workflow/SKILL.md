---
name: gas-clasp-workflow
description: Google Apps Script (GAS) 本地開發與自動同步 (clasp) 工作流。支援自動 push、pull、專案初始化與部署。
---

# GAS Clasp 開發與自動同步工作流

本技能提供 Google Apps Script (GAS) 本地開發與自動同步 (clasp) 的標準化指令與工作流程。

## 觸發情境
當提到以下內容時載入本技能：
- 「GAS」、「Google Apps Script」、「clasp」
- 「推送」、「部署到 GAS」、「更新 GAS 程式碼」、「push」
- 「下載 GAS 程式碼」、「從雲端拉取」、「pull」

## 核心指令指引
因為系統中已安裝 `@google/clasp` 且已完成 `clasp login`，請一律使用 `npx @google/clasp` 執行相關命令以避免路徑或環境變數問題。

1. **同步代碼到雲端 (Push)**：
   當修改完成或使用者要求同步/部署時，在專案目錄下執行：
   ```powershell
   npx @google/clasp push
   ```
   *注意：若有修改 `.claspignore`，需注意是否忽略了非必要的檔案。*

2. **拉取雲端代碼到本地 (Pull)**：
   當雲端程式碼有更新，或需要同步回本地時：
   ```powershell
   npx @google/clasp pull
   ```

3. **連結現有專案 (Clone)**：
   在空目錄中連結現有 GAS 專案：
   ```powershell
   npx @google/clasp clone "<SCRIPT_ID>"
   ```

4. **建立全新專案 (Create)**：
   在空目錄中建立全新專案並與雲端連結：
   ```powershell
   npx @google/clasp create --title "<專案名稱>" --type <sheets|docs|slides|forms|web|api>
   ```

5. **查看部署版本 (Deployments)**：
   ```powershell
   npx @google/clasp deployments
   ```

## 自動化原則
- **修改後自動提示**：當你在本地為使用者修改或新增了 GAS 檔案（如 `.js` 檔或 `.html` 檔）後，請主動詢問或直接執行 `npx @google/clasp push`。
- **無縫轉換**：GAS 本地檔案後綴為 `.js`，上傳到雲端後會自動變為 `.gs`。請在本地端保持使用 `.js` 或 `.html` 開發。
- **確認 API 開啟**：如果 `clasp` 報錯「Google Apps Script API is not enabled...」，請引導使用者至 https://script.google.com/home/usersettings 啟用該 API。
