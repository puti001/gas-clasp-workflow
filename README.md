# Antigravity GAS Clasp 自動化開發技能包

這是一個專為 AI Agent（如 Antigravity / Opencode / Gemini 等）設計的**自訂技能與規則包**。

> 💡 **你是剛接觸 AI Agent 的初學者小白嗎？**
> 請直接點選閱讀 👉 [**🤖 小白專用：如何指揮你的 AI 學習此技能指南**](./AGENT_GUIDE.md)

安裝後，AI Agent 將會學會使用 Google 官方的 `clasp` 工具，並在開發 Google Apps Script (GAS) 專案時，於本地修改代碼後**自動將程式碼 push 到雲端**，免去你手動複製貼上前硬體端與後端代碼的痛苦。

---

## 📂 專案結構

- `.agents/skills/gas-clasp-workflow/SKILL.md`：定義了 clasp 的基礎指令與 AI 運作流程。
- `.agents/rules/gas-clasp-workflow.md`：自訂規則，告訴 AI 只要是 GAS 專案就必須在修改完成後自動 `clasp push`。

---

## 🚀 如何讓你的 AI 學習此技能？

你可以選擇**全域安裝**（推薦，所有專案皆適用）或**專案級安裝**：

### 1. 全域安裝 (Global)
將此 repo 中的設定複製到你電腦的 AI 全域設定目錄中：

- **Windows 預設路徑**：`C:\Users\<你的使用者名稱>\.gemini\config\`
  1. 將 `.agents/skills/gas-clasp-workflow` 資料夾複製到 `C:\Users\<Username>\.gemini\config\skills\` 目錄下。
  2. 將 `.agents/rules/gas-clasp-workflow.md` 的規則內容，複製貼到 `C:\Users\<Username>\.gemini\config\AGENTS.md` (或 `GEMINI.md`) 檔案的末尾。

- **Mac/Linux 預設路徑**：`~/.gemini/config/`
  - 同理，將技能放入 `~/.gemini/config/skills/`，並將規則加入 `~/.gemini/config/AGENTS.md`。

### 2. 專案級安裝 (Workspace)
如果你只想在特定 GAS 專案中使用：
- 直接將本專案的 `.agents` 資料夾複製並放到你的專案根目錄下即可。

---

## 🛠️ 事前準備（使用者端）

為了讓 AI 能順利與 Google 雲端通訊，請在你的電腦上完成以下兩步驟：

1. **全域安裝 clasp**：
   ```bash
   npm install -g @google/clasp
   ```
2. **登入 Google 帳號**：
   ```bash
   clasp login
   ```
3. **啟用 Google Apps Script API**：
   前往 [Google Apps Script 使用者設定](https://script.google.com/home/usersettings) 將 **Google Apps Script API** 設為 **啟用 (ON)**。

---

## 🎮 使用方法

當 AI 載入此技能後，你只要對 AI 說：
> 「幫我 clone 現有的 GAS 專案，Script ID 是 `xxxxxx`」

或是：
> 「幫我建立一個新的 Sheets GAS 專案」

之後，你在本地讓 AI 修改任何代碼，修改完後 **AI 會自動在終端機跑 `clasp push`**。你只需要在瀏覽器重新整理 GAS 編輯器網頁，就能立刻看到最新結果！

---

*本專案由 [屏東縣後庄國小黃朝榮老師](https://padlet.com/clongwh/puti_ai_tools) 免費分享，歡迎擴散推廣！*

---

## 💖 特別致謝

本專案在開發與改進過程中，特別參考並借鑒了 **三師爸** 的優秀開源專案 [clasp-gas-skill](https://github.com/mathruffian-dot/clasp-gas-skill)，吸取了其中關於 clasp v3 指令相容、防止網址拼接出錯、退場機制與個資防護等先進的 AI 技能設計原則。在此致敬並感謝其對開源社群的貢獻！

