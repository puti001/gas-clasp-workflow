# GAS Clasp 自動化規則

- **觸發條件**：當開發 GAS (Google Apps Script) 專案時（專案目錄中含有 `.clasp.json` 或 `appsscript.json`）。
- **執行規則**：
  1. 在本地端程式碼修改完成後，AI 必須主動執行或詢問使用者是否執行 `npx @google/clasp push` 將程式碼自動同步部署至雲端，免去手動複製貼上。
  2. 若需要從雲端同步回本地，執行 `npx @google/clasp pull`。
  3. 當使用者提及「部署」、「推送」、「上傳」、「同步到 GAS」時，請直接執行 `npx @google/clasp push`。
