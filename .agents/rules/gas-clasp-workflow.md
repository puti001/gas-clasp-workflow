# GAS Clasp 自動化規則

- **觸發條件**：當開發 GAS (Google Apps Script) 專案時（專案目錄中含有 `.clasp.json` 或 `appsscript.json`）。
- **執行規則**：
  1. 在本地端程式碼修改完成後，AI 必須主動執行或詢問使用者是否執行 `npx @google/clasp push` 將程式碼自動同步部署至雲端，免去手動複製貼上。
  2. 若需要從雲端同步回本地，執行 `npx @google/clasp pull`。
  3. **必須使用 clasp v3 指令**（如 `create-script`、`clone-script`、`list-deployments`、`create-deployment` 等），切勿使用舊版 v2 廢棄指令。
  4. **嚴禁自行用 scriptId 拼接網頁應用程式網址**。必須使用 `npx @google/clasp open-web-app <deploymentId> --json` 獲取真實網址。
  5. 嚴禁在程式碼或試算表中寫入真實姓名、電話等個人隱私個資。
  6. 若連續失敗兩次，必須自動退回「提供代碼供使用者手動複製貼上」的降級方案，不可陷入重試死循環。
