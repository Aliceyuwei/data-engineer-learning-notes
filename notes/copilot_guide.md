# 🤖 AI Copilot & Continue 終極使用指南

> **當前配置：** GitHub Copilot (自動補全) + Continue (專案架構與數據管線)

---

## ⌨️ 核心快捷鍵 (已優化衝突)

| 功能 | 說明 | 快捷鍵 |
| :--- | :--- | :--- |
| **Inline 補全** | 打字時自動出現灰色代碼 (Copilot 驅動) | `Tab` 接受 / `Esc` 拒絕 |
| **Inline Edit** | **選取程式碼後要求修改 (GitHub Copilot)** | `Cmd + I` |
| **Ask Anything** | **開啟側邊對話視窗 (Continue - Gemini 2.5 Pro)** | `Cmd + L` |
| **Quick Chat** | 快速問答，不開啟側邊欄 | `Cmd + Shift + Alt + L` |

---

## 🛠️ Edit Mode 指令大全 (`#` Context Tags)
**使用時機：** 在代碼框中使用 `#` 符號引發背景資訊，讓 AI 精準修改代碼。

| 指令 | 說明與用途 |
| :--- | :--- |
| **`#codebase`** | 參考整個專案的內容與符號，適用於跨檔案修改。 |
| **`#file`** | 參考指定的單一或多個檔案內容。 |
| **`#selection`** | 僅針對目前選取的代碼片段進行分析。 |
| **`#sym`** | 參考特定的 Symbol (如變數名、函式名)。 |
| **`#terminalSelection`** | 參考妳在終端機選取的報錯資訊。 |
| **`#terminalLastCommand`** | 參考前一個執行的終端機指令及其輸出。 |
| **`#installPythonPackage`** | 偵測缺少的庫並生成 `pip install` 指令。 |
| **`#configurePythonEnvironment`** | 自動化配置 Python 虛擬環境。 |
| **`#vscodeAPI`** | 開發 VS Code 插件時使用的專用參考。 |
| **`#local_files`** | 可直接引用如 `month1_ai_learning_data_pipeline.md` 等本地文件。 |

---

## 💬 Ask Mode 指令大全 (`@` Providers / `/` Commands)
**使用時機：** 在側邊欄 (`Cmd+L`) 進行深度討論或專案規劃。

### 1. 知識來源定位 (Context Providers - `@`)
* **`@workspace`**：掃描整個工作區，詢問整體架構問題。
* **`@github`**：查詢網路資料、開源庫代碼或 Web 搜尋。
* **`@terminal`**：直接讀取終端機當前的所有輸出。
* **`@vscode`**：操作 VS Code 本身的功能。
* **`@history`**：參考最近的修改紀錄或對話歷史。
* **`@docs`**：使用妳手動加入的官方文件 (如 Python 3, SQLite)。

### 2. 任務動作指令 (`/`)
* **`/explain`**：逐行解釋代碼邏輯。
* **`/fix`**：針對 Bug 提供修正建議。
* **`/new`**：生成全新模組、組件或檔案。
* **`/newNotebook`**：**數據學習必備**：直接生成 `.ipynb` 筆記檔。
* **`/tests`**：為函式自動生成單元測試。
* **`/setupTests`**：初始化專案的測試環境。
* **`/fixTestFailure`**：分析並修復失敗的測試案例。
* **`/search`**：調用 VS Code 全域搜尋。
* **`/startDebugging`**：直接啟動除錯模式。
* **`/clear`**：清除對話紀錄並重置。

---

## ⚙️ 專業配置設定 (Settings.json)

```json
{
  "github.copilot.enable": { "*": true },
  "continue.enableTabAutocomplete": false, // 關掉 Continue 補全，讓 Copilot 專心做
  "continue.models": {
    "chat": "google/gemini-2.5-pro",
    "edit": "google/gemini-2.5-pro"
  },
  "continue.indexing.enabled": true // 開啟 @workspace 必備的代碼索引功能
}