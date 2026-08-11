# 🤖 小白必看：如何指揮你的 AI 學習這個 GAS 同步技能？

如果你是剛接觸 AI Agent（如 Cursor, Windsurf, Antigravity 等）的初學者，不知道該怎麼讓你的 AI 學會這個「修改完 GAS 程式碼自動同步，免複製貼上」的神技，請跟著以下步驟做！

---

## 步驟一：把這個「技能包」下載並放進你的專案中

1. 下載這個 GitHub 專案的所有檔案（你可以點擊 GitHub 右上角的 **Code** -> **Download ZIP** 並解壓縮）。
2. 在你的電腦上，建立一個你準備用來開發 Google Apps Script 的新資料夾（例如 `my-gas-app`）。
3. 把解壓出來的 **`.agents`** 這個資料夾，複製並整包貼進你的 `my-gas-app` 資料夾中。
   *（備註：在 Mac 或 Windows 上，以 `.` 開頭的資料夾可能會被系統隱藏，如果不見了，請在系統設定中開啟「顯示隱藏的檔案與資料夾」）*

---

## 步驟二：如何指揮你的 AI？（複製以下 Prompt 給它）

當你用你的 AI 編輯器（例如 Cursor、Windsurf、或 Antigravity）開啟你的專案資料夾後，請在對話框裡**直接複製貼上**這段話給你的 AI：

> 💬 **給 AI 的指令（直接複製）**：
> 「這是我用來開發 Google Apps Script 的本地專案。請讀取專案根目錄下 `.agents/skills/gas-clasp-workflow/SKILL.md` 的技能檔案，以及 `.agents/rules/gas-clasp-workflow.md` 的規則。
> 
> 從現在起，你必須遵守這個規則：**只要你在本地修改或新增了任何代碼（包括前端 .html 或後端 .js 檔案），修改完成後請自動在終端機執行 `npx @google/clasp push` 同步至雲端。** 不需要我手動複製貼上。請回覆我『我已理解並載入此技能』。」

此時，你的 AI 就會讀取規則，並且「聽話」地載入這個自動同步的工作流。

---

## 步驟三：日常開發的指揮暗號（實戰語句）

當你的 AI 學會這個技能後，你可以用以下這幾句「魔法指令」指揮它：

### 🎯 暗號 1：把雲端的現有專案拉下來
> 💬 「幫我 clone 雲端專案，Script ID 是 `你的_SCRIPT_ID`」
> *（AI 會在本地下載你雲端本來的程式碼）*

### 🎯 暗號 2：請它寫程式並自動上傳
> 💬 「幫我在 Google 試算表新增一個選單按鈕，並在本地端寫好代碼後直接 push 到 GAS 雲端」
> *（AI 寫完代碼後，會自動在背景執行 push，你只需去瀏覽器重新整理 GAS 網頁即可看見最新成果！）*

### 🎯 暗號 3：從雲端把最新代碼拉回本地
> 💬 「我剛剛在網頁端改了代碼，幫我 pull 回本地更新檔案」

---

## ⚠️ 常見的踩坑與解決辦法 (Q&A)

### Q1：AI 執行 `clasp` 時報錯「Google Apps Script API is not enabled...」？
* **解法**：這是因為你的 Google 帳號還沒開啟 API 權限。請用瀏覽器打開這個網址：[Google Apps Script 使用者設定](https://script.google.com/home/usersettings)，並將最下方的 **Google Apps Script API** 切換為 **啟用 (ON)** 即可。

### Q2：AI 執行 `clasp` 時顯示未登入？
* **解法**：在你的電腦終端機手動輸入以下指令，瀏覽器會跳出視窗，讓你點選你的 Google 帳號完成登入授權即可！
  ```bash
  clasp login
  ```
