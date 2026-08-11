# Google Apps Script 本地自動同步開發說明

此工作區已整合 **`clasp`** 開發流程。未來開發 GAS 時，我會自動幫你將本地修改推送（push）到雲端，你再也不需要手動複製貼上！

## 如何開始新專案或連結現有專案？

### 方式 A：連結你現有的雲端 GAS 專案（推薦）
1. 建立一個新資料夾（例如 `my-gas-project`）並進入該資料夾。
2. 取得你的雲端專案 **Script ID**（在專案設定的「Script ID」欄位中複製）。
3. 請我執行，或自行在終端機輸入：
   ```powershell
   npx @google/clasp clone "<YOUR_SCRIPT_ID>"
   ```
4. 這會自動把雲端程式碼下載到本地。

### 方式 B：建立一個全新的專案
1. 建立一個新資料夾並進入。
2. 請我執行，或自行在終端機輸入：
   ```powershell
   npx @google/clasp create --title "專案名稱" --type <sheets|docs|slides|forms|web|api>
   ```

---

## 日常開發流程

1. **修改代碼**：我會在本地為你修改 `.js`（會自動同步為 `.gs`）或 `.html` 檔案。
2. **自動同步**：代碼修改完成後，我會自動在背景為你執行：
   ```powershell
   npx @google/clasp push
   ```
3. **即時生效**：你只需回到 Google Apps Script 瀏覽器編輯器中**重新整理頁面**，就能看到最新代碼！

> [!NOTE]
> 如果 `clasp` 提示 API 未啟用，請前往 [Google Apps Script 使用者設定](https://script.google.com/home/usersettings) 將 **Google Apps Script API** 設為 **啟用 (ON)**。
