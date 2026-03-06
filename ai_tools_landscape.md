# AI Tools Landscape（目前常見 AI 工具整理）

> 目的：用「分類 + 代表工具 + 適用情境」快速掌握現階段常見 AI 工具。\
> 備註：這份清單不追求完整（工具更迭很快），重點是建立可持續更新的分類框架。

------------------------------------------------------------------------

## 1 對話式 AI / 知識助理（Chat / Q&A）

適合：問答、寫作、摘要、腦力激盪、需求釐清、語意理解。

- **ChatGPT**：通用對話、寫作、分析、工具整合生態大
- **Claude**：長文閱讀/改寫、文件理解與寫作常見選擇 我沒有
- **Gemini**：多模態（文字/圖像/檔案）與 Google 生態整合。深入用法特長：
  - **Deep Research**：適合進行深度搜尋、跨網頁資料彙整與長篇報告分析。
  - **引導式學習**：可做為私人導師，幫你規劃階段性學習路徑並逐步引導。
  - **直接生成前端網頁**：結合 **Canvas** 模式，能直接幫你寫出前端網頁，並在介面旁開啟即時預覽（Live Preview），方便邊看邊修改。
- **NotebookLM**：Google 推出的知識助理，專打「基於你的資料來源回答」。
  - **匯入程式碼與文件**：可以上傳程式碼檔案、PDF、Google 雲端硬碟文件。
  - **精準索引**：AI 的回答會嚴格基於你上傳的資料來源，並附上引用位置，非常適合用來理解複雜專案或長篇官方文檔。
- **Perplexity**：偏「搜尋 + 引用來源」的問答體驗

------------------------------------------------------------------------

## 2 開發用 AI 工具（Coding Assistants / Coding Agents / Model Prototyping Tools）

> 分類原則：
> - 第一層：主要互動介面（IDE / Terminal / Cloud）
> - 第二層：自主程度（Assistive / Agentic / Autonomous）

### 2.1 IDE 內嵌型助理（IDE-Integrated Assistants）

適合：補全、局部重構、解釋程式碼、生成測試、寫文件。  
特徵：以 IDE 為中心，偏向「你主導，AI 輔助」。

- **GitHub Copilot**：補全、Chat、測試生成、程式解釋，覆蓋面廣
- **Codeium**：補全 / Chat 類型替代方案
- **Tabnine**：企業與團隊管控場景常見
- **Continue（基礎模式）**：可接多模型與本地模型，高度可自訂

---

### 2.2 IDE 型 Agent（IDE-Centric Coding Agents）

適合：跨檔案修改、深度重構、整包功能調整、在 IDE 中交辦任務。  
特徵：以 IDE 為主介面，但 Agent 可自主探索 codebase、改多檔、跑指令、迭代修正。

- **Cursor**：AI editor + coding agent，適合整包改動與深度重構
- **Continue（Agent mode）**：可透過 MCP / tools 擴充，適合自訂工作流
- **Google Antigravity**：Agent-first 開發平台，屬於 IDE / 平台型 autonomous agent

---

### 2.3 Terminal 助理（CLI / Terminal Assistants）

適合：查命令、生成 shell script、解釋 terminal 錯誤、提升命令列效率。  
特徵：以 terminal 為主，但偏輔助，不強調完整自主 coding 流程。

- **Copilot CLI**
- **Fig**
- **ShellGPT**
- **Warp AI（基礎命令輔助用法）**

---

### 2.4 Terminal 型 Coding Agents（CLI-Native Coding Agents）

適合：在 terminal 中交辦多步驟 coding 任務、跨檔案修改、自主偵錯與修復。  
特徵：介面是 CLI，但已具備 agentic loop 與工具操作能力。

- **Gemini CLI**
- **Claude Code**
- **aider**

---

### 2.5 雲端 / 背景執行型 Coding Agents（Cloud / Background Coding Agents）

適合：Issue-to-PR、自動處理重複任務、平行代理工作流。  
特徵：Agent 可在背景或雲端環境工作，完成後回傳 PR / 結果。

- **OpenAI Codex**
- **GitHub Copilot coding agent**

---

### 2.6 模型 Playground / API 原型工具（Model Playground / API Prototyping Tools）

適合：測試 Prompt、比較模型表現、調整參數、安全設定、函式呼叫、結構化輸出，並快速產出 API 範例程式。  
特徵：不是日常寫專案 code 的主力編輯器，也不是自主 coding agent；核心用途是「先把模型行為試對，再接進你的應用」。

- **Google AI Studio**：Google 的 Gemini 模型實驗台與原型開發入口，可用來測 prompt、調整 run settings、啟用 structured output / function calling / code execution / grounding、取得與管理 API key、監看用量，並透過 **Get code** 產出範例程式後接回正式專案。
除了測 prompt、管理 API key、監看用量，也可透過內建 code editor 與 build mode，
直接生成、編輯、執行與部署前端或 full-stack app prototype。
------------------------------------------------------------------------

## 3 Agent / 工作流自動化（把「對話」變「執行」）

適合：把一串任務（查資料→整理→寫入工具→通知）做成可重複流程。

- **Microsoft AutoGen**：多 agent 協作與對話式編排的常見選項
- **OpenClaw**：開源 agent / 工具執行生態，重點在把「工具/技能」編排成可控、安全、可追蹤的自動化流程

- **LangGraph**：用「狀態機/圖」方式做可控的 agent flow
- **LangChain**：常見的 LLM 應用組裝工具（工具調用、RAG、鏈式流程）
- **LlamaIndex**：偏資料/索引/RAG 管線整合（文件到檢索到回覆）
- **LobsterAI（有道，非 OpenClaw）**：另一個同名方向的開源 AI agent 產品（避免與 OpenClaw 的 Lobster 混淆）
- **n8n / Zapier / Make / Pipedream**：低碼自動化（接各種 SaaS、排程、Webhook）

------------------------------------------------------------------------

## 4 RAG / 向量資料庫（讓模型「用你的資料回答」）

適合：公司文件、筆記、規範、FAQ、知識庫；需要可追溯來源與持續更新。

- **向量資料庫**：
    - **Pinecone**（託管）
    - **Weaviate**（自架/託管）
    - **Milvus**（自架常見）
    - **Qdrant**（自架常見）
    - **Chroma**（輕量原型常見）
- **RAG 框架**：**LlamaIndex / LangChain / Haystack**
- **重點概念（方便你後續補章節）**：chunking、embedding、rerank、hybrid search、citations、資料更新策略

------------------------------------------------------------------------

## 5 影像 / 影片生成與編修（Multimodal / Creative）

適合：行銷素材、插圖、原型視覺、短影片、分鏡、風格化。

- **Midjourney**：偏風格化圖像生成社群常見
- **Stable Diffusion（含各種 UI/平台）**：可自訂、可本地化的擴散模型生態
- **Adobe（Firefly / Photoshop 等）**：與設計工作流整合、商業素材流程常見
- **Runway**：影片生成/剪輯輔助常見

------------------------------------------------------------------------

## 6 語音（TTS / STT / 會議紀錄）

適合：錄音轉文字、逐字稿、會議摘要、配音、客服語音流程。

- **Whisper / 相關封裝服務**：常見的語音轉文字基礎
- **ElevenLabs（TTS）**：常見的自然語音合成選項
- **會議工具（Notion / Google / Microsoft 等生態內建）**：偏「錄→轉→摘要→行動項目」整合

------------------------------------------------------------------------

## 7 評測 / 監控 / 可觀測性（讓 AI 應用可上線）

適合：你要把 AI 做成產品或內部工具時，追蹤品質、成本、延遲、失敗案例。

- **LangSmith**：LangChain 生態的 trace/eval 常見方案
- **Langfuse**：開源取向的 tracing / prompt / eval 管理常見
- **Helicone**：API proxy + 觀測（記錄用量/延遲/成本）
- **Ragas / DeepEval / promptfoo**：RAG 與 LLM 回覆品質評估常見工具

------------------------------------------------------------------------

## 8 Prompt / 模板與知識資產管理（把提示詞變可維護）

適合：團隊共用提示詞、版本控管、A/B 測試、模板化輸入輸出。

- **PromptLayer**：提示詞與請求紀錄、版本與評估常見選項
- **Langfuse（prompt 管理）**：常見的開源整合做法
- **（也可用你自己的 repo + 測試腳本）**：最可控、最符合工程化流程

------------------------------------------------------------------------

## 9 模型供應商 / 平台（API 與企業整合）

適合：要穩定 API、權限控管、合規、用量管理、企業採購。

- **OpenAI / Anthropic / Google**：主流雲端模型供應
- **AWS Bedrock / Azure OpenAI**：企業雲端採用常見路徑（權限/網路/合規）
- **Cohere / Mistral 等**：視語言、成本、部署策略評估

------------------------------------------------------------------------

## 10 本地模型與推論（Local / On-prem / 離線）

適合：資料敏感、離線環境、成本控制、可自訂部署。

- **Ollama**：本地拉模型與快速啟動常見
- **llama.cpp**：CPU/輕量部署常見
- **vLLM**：高吞吐推論服務常見（偏服務端）

------------------------------------------------------------------------

## 11 微調 / 訓練（把模型更貼近你的任務）

適合：固定格式輸出、領域語言、特定分類/抽取、成本/延遲優化（視情境）。

- **PEFT / LoRA 生態**：常見的參數高效微調方式
- **Axolotl 等訓練腳手架**：快速跑微調流程的常見工具
- **重點概念**：資料品質 > 量；先做 eval；先確認是否 RAG 就夠用

------------------------------------------------------------------------

## 12 資料標註 / 合成資料（讓訓練與評測有料）

適合：分類/抽取任務的標註、建立測試集、弱監督與資料管線。

- **Label Studio**：開源標註工具常見
- **Scale AI**：商業標註服務常見
- **Snorkel**：弱監督/規則標註的常見方向

------------------------------------------------------------------------

# AI 開發工具配置與分工說明

## 目的

這份文件整理我目前的 AI 開發工具配置，並說明各工具的定位、個別優勢、適合負責的工作，以及整體最佳分工方式。

我目前的核心目標不是把所有工具混在一起用，而是讓每個工具負責自己最擅長的環節，避免互相重疊、互相干擾。

---

## 我目前的開發配置

- **主編輯器**：VS Code
- **即時補全工具**：GitHub Copilot
- **規劃 / 架構思考工具**：Continue
- **可考慮補充的 GitHub / PR Agent**：Copilot coding agent
- **可考慮補充的進階 Agent 平台**：Google Antigravity
- **可考慮補充的模型 Playground / API 原型工具**：Google AI Studio

---

## 整體配置理念

目前這套配置的核心思路是：

- **VS Code** 負責本地開發主工作台
- **Copilot** 負責寫 code 當下的即時補全與局部輔助
- **Continue** 負責整體架構規劃、需求拆解、方案比較與專案脈絡理解
- **Copilot coding agent** 適合接 GitHub issue、分支、PR 這類背景執行任務
- **Google Antigravity** 適合處理更完整的 agent-first 工作流，例如跨 editor、terminal、browser 的端到端任務
- **Google AI Studio** 適合用來測試 Gemini 模型、實驗 Prompt、調整模型參數與產出 API 原型程式

簡單來說：

> **Continue 負責想清楚，Copilot 負責寫得快，Copilot coding agent 負責 GitHub / PR 流程，Antigravity 負責更重的 agent-first 任務流程。**

---

## 各工具個別優勢

### 1. VS Code

**定位**：主編輯器 / 本地開發工作台

**優勢**：

- 生態成熟，擴充套件多
- 語言支援完整
- 除錯、測試、Git 整合成熟
- 本地開發體驗穩定
- 適合作為所有 AI 工具的承載平台

**適合負責**：

- 日常 coding
- 專案檔案管理
- 除錯與測試
- 本地開發主流程

**不適合負責**：

- 自主規劃任務
- 長鏈 AI agent 執行流程

---

### 2. GitHub Copilot

**定位**：IDE 內即時補全與局部程式輔助工具

**優勢**：

- 補全速度快，低干擾
- 適合逐行或小區塊生成程式碼
- 適合局部重構與小範圍修正
- 可快速生成測試、註解、樣板碼
- 在寫 code 當下最順手

**適合負責**：

- 即時補全
- 小段函式生成
- 小範圍重構
- 測試樣板生成
- 小段程式碼解釋

**不適合負責**：

- 大型架構規劃
- 跨大量檔案的整包重構
- 長鏈任務拆解
- 複雜的專案級決策

**我目前對它的使用定位**：

> Copilot 主要就是用來做代碼補全，讓我在手動 coding 當下更快。

---

### 3. Continue

**定位**：架構規劃工具 + 專案脈絡理解工具 + 可進一步升級為本地 Agent

**優勢**：

- 對整體專案架構思考能力較強
- 適合需求拆解、方案比較、模組規劃
- 能從 repo 脈絡理解整體系統
- 可接不同模型，具備彈性
- 若開啟 Agent 能力，可進一步執行多步驟修改、跑命令、修 bug

**適合負責**：

- 系統架構規劃
- 功能拆解
- 影響面分析
- 需求轉任務
- 跨檔案脈絡理解
- 前期設計與落地步驟規劃

**不適合負責**：

- 當作單純即時補全工具
- 取代 GitHub PR 流程中心
- 處理純背景型 issue-to-PR 自動交付流程

**我目前對它的使用定位**：

> 我會用 Continue，是因為它在規劃整體架構這件事上比較強。

這代表 Continue 在我的工具鏈裡，不只是聊天工具，而是偏向「技術規劃師」與「專案層級理解器」。

---

### 4. Copilot coding agent

**定位**：GitHub / Issue / PR 流程導向的背景型 coding agent

**優勢**：

- 適合接 GitHub issue 並轉成實作
- 可在背景工作後產出 PR
- 與 GitHub 工作流對位度高
- 適合分支、commit、PR review 流程
- 很適合明確邊界的任務交辦

**適合負責**：

- issue 對應的小功能
- 明確 bug 修復
- PR follow-up 修改
- 背景產出可 review 的改動

**不適合負責**：

- 模糊需求探索
- 大型架構設計
- 長時間來回討論需求
- 前期方案比較

**我對它的使用建議**：

> GitHub / PR 流程通常交給 Copilot coding agent 會比 Continue 更對位。

原因是 Continue 更適合想清楚、拆清楚、規劃清楚；Copilot coding agent 更適合在需求已經明確後，幫我把 GitHub 任務流接起來。

---

### 5. Google Antigravity

**定位**：Agent-first 開發平台 / 進階型 IDE Agent 工作台

**優勢**：

- 強調 agent-first 工作流
- 可讓 agent 跨 editor、terminal、browser 執行任務
- 適合多步驟、長鏈、端到端任務
- 強調任務編排與多 agent 管理
- 能把開發、驗證、甚至部署納入同一條流程
- 對 Google Cloud 路線特別有吸引力

**適合負責**：

- 端到端功能實作流程
- 長鏈自動化任務
- 跨工具執行與驗證
- 想減少手動切換 editor / terminal / browser 的場景
- 想把驗證與部署也放進 agent 流程的場景

**不適合負責**：

- 只想要單純補全的人
- 只想保留傳統 VS Code 手動 coding 體驗的人
- 還不確定自己是否真的需要 agent-first 工作流的人

**關於它的定位補充**：

Google Antigravity 的優勢不是單純「能部署」，而是：

> 它更擅長把「寫程式 → 執行 → 驗證 → 部署」串成一條 agent workflow。

所以它不是單純的 VS Code 替代品，而比較像是：

> **可以當編輯器使用的 agent-first 開發平台。**

---

---

### 6. Google AI Studio

**定位**：模型 Playground / Gemini API 原型開發工具 / Prompt 實驗台

**優勢**：

- 適合快速測試 Gemini 模型與 Prompt 行為
- 可調整模型參數、Safety 設定與工具能力
- 可試驗 structured output、function calling、code execution、grounding 等能力
- 可建立與管理 Gemini API key
- 可直接產出範例程式碼，再接回正式專案
- 適合在實作前先驗證模型是否符合需求

**適合負責**：

- Prompt 實驗
- 模型比較與選型
- Gemini API 原型驗證
- function calling / structured output 設計
- 取得 API key 與前期接入測試

**不適合負責**：

- 當主編輯器使用
- 取代 VS Code / Cursor 進行日常 coding
- 取代 GitHub / PR agent 工作流
- 執行完整的多步驟本地 coding 任務

**我對它的使用定位**：

> Google AI Studio 不是拿來取代編輯器或 coding agent 的，而是用來先把 Gemini 的模型行為、Prompt、參數與 API 接法試對。

這代表它在我的工具鏈裡，比較像是：

> **模型實驗台 + API 原型開發入口**

而不是日常 coding 主力。


## 最佳分工建議

### VS Code
負責：

- 主編輯器
- 本地開發
- 除錯
- 一般日常 coding

### GitHub Copilot
負責：

- 代碼補全
- 小範圍生成與改寫
- 快速補測試與樣板碼

### Continue
負責：

- 整體架構規劃
- 模組切分
- 需求拆解
- 專案脈絡理解
- 技術方案比較
- 前期實作步驟設計

### Copilot coding agent
負責：

- GitHub issue 對應任務
- branch / commit / PR 導向的背景工作
- 邊界清楚的小功能與 bugfix

### Google Antigravity
負責：

- 更完整的 agent-first 任務流
- 跨 editor / terminal / browser 的執行流程
- 想把驗證與部署納入同一條任務流時使用

### Google AI Studio
負責：

- 測試 Gemini 模型與 Prompt
- 驗證 structured output / function calling / code execution 等能力
- 建立與管理 Gemini API key
- 產出 API 原型範例程式後再接回正式專案

---

## 建議工作流

### 工作流 1：規劃階段
先用 **Continue**：

- 分析需求
- 拆模組
- 看影響面
- 定義實作步驟
- 決定哪些任務應切成 GitHub issue

### 工作流 2：手動實作階段
回到 **VS Code + Copilot**：

- 手動寫主要程式
- 用 Copilot 提高輸入效率
- 做局部補全與小範圍重構

### 工作流 3：明確任務交辦
把邊界清楚的任務交給 **Copilot coding agent**：

- issue 明確
- 修 bug 路徑清楚
- 功能小而完整
- 想直接產出 PR 給自己 review

### 工作流 4：模型實驗與 API 原型
先用 **Google AI Studio**：

- 測試 Gemini 模型是否適合任務
- 調整 Prompt、模型參數與工具能力
- 驗證 structured output / function calling 等設計
- 產出範例程式碼，再接回正式專案

### 工作流 5：進階 agent-first 流程
在需要時再導入 **Google Antigravity**：

- 讓 agent 自己跨 editor / terminal / browser 執行
- 把開發、驗證、部署串起來
- 減少手動切換上下文

---

## 我目前最適合的結論

以我目前的狀況來看，最合理的核心配置不是全部重換，而是：

- **VS Code** 當主編輯器
- **Copilot** 做即時補全
- **Continue** 做架構規劃與專案級理解
- **Copilot coding agent** 補上 GitHub / PR 導向的背景 agent 能力
- **Google AI Studio** 作為 Gemini 模型實驗與 API 原型工具，在接入前先驗證模型行為
- **Google Antigravity** 作為進階型 agent 平台，在需要更完整端到端流程時再導入

這樣的好處是：

1. 保留我已經熟悉的 VS Code 工作流
2. 不浪費 Copilot 在補全上的優勢
3. 持續發揮 Continue 在整體規劃上的強項
4. 用 Copilot coding agent 補齊 GitHub / PR 自動化流程
5. 用 Google AI Studio 先做 Gemini 模型與 API 原型驗證，避免直接在正式專案裡試錯
6. 讓 Antigravity 成為未來升級 agent-first workflow 的選項，而不是現在就硬切主力工具

---

## 最終一句話總結

> **我目前最適合的配置是：VS Code 當主工作台，Copilot 負責補全，Continue 負責規劃與架構，Copilot coding agent 負責 GitHub / PR 流程，Google AI Studio 負責 Gemini 模型與 API 原型驗證，而 Google Antigravity 作為更進階的 agent-first 工作台保留在需要時導入。**

