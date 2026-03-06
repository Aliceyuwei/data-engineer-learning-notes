# 🚀 180 天 AI-Native Data Engineer Roadmap

> 目標：從前端工程師轉型為具備 **資料工程（Data Engineering）能力** 的工程師  
> 工具導向：**VS Code + Copilot + Gemini CLI**

------------------------------------------------------------------------

# Month 1 --- Python 與第一個 ETL 系統

## Week 1 --- Python 專案與 Markdown Parser

**本週任務**

建立 Python 專案並熟悉 VS Code + Copilot + Gemini CLI 的 AI 協作開發流程。使用 VS Code + Copilot + Gemini CLI 建立專案骨架，包含資料夾結構、`requirements.txt`、`README.md`。實作 Markdown 解析器，將學習筆記中的標題與內容轉為結構化資料（JSON）。

**實作清單**

- [ ] 專案環境初始化
  - [ ] 建立 `ai-learning-data-pipeline` 專案目錄與 Git 初始化
  - [ ] 建立標準資料夾結構 (`src/`, `data/`, `tests/`)
  - [ ] 配置 `.gitignore` 與 `requirements.txt`
- [ ] 定義資料規範
  - [ ] 制定學習筆記的 Markdown 格式標準
  - [ ] 建立測試用的範例 Markdown 檔案
- [ ] 核心解析器開發
  - [ ] 實作 `markdown_parser.py`：負責將非結構化文字轉為 Python Dict
  - [ ] 實作錯誤處理機制（例如：日期格式錯誤、欄位缺失）
- [ ] 品質保證與工具化
  - [ ] 撰寫 `pytest` 單元測試，涵蓋正常與異常情境
  - [ ] 封裝 `main.py` 為 CLI 工具，支援指定檔案解析並輸出 JSON

**本週核心觀念**

- Data Pipeline 是什麼
- ETL (Extract → Transform → Load)
- 結構化資料 vs 非結構化資料
- VS Code + Copilot + Gemini CLI 協作開發流程

------------------------------------------------------------------------

## Week 2 --- 建立 ETL Pipeline

**本週任務**

建立簡單 ETL pipeline。讀取 Markdown 檔案 → 解析 → 存入 SQLite。重構程式碼，將 parser、etl、db 操作拆成不同模組。

**本週核心觀念**

- Pipeline 架構
- Single Responsibility Principle
- 資料流設計
- Logging 與錯誤處理

------------------------------------------------------------------------

## Week 3 --- Telegram 通知

**本週任務**

建立 Telegram Bot。當 ETL pipeline 完成時，將每日新增資料摘要傳送到 Telegram。

**本週核心觀念**

- Event-driven notification
- API integration
- Token 與環境變數管理

------------------------------------------------------------------------

## Week 4 --- 程式品質與測試

**本週任務**

加入 logging、錯誤處理與基本測試。使用 VS Code + Copilot + Gemini CLI 生成 unit test 並改善程式結構。

**本週核心觀念**

- 可維護程式碼
- Logging 系統
- Unit testing 基本概念

------------------------------------------------------------------------

# Month 2 --- 職缺資料來源（小龍蝦爬蟲）

## Week 5 --- 小龍蝦部署

**本週任務**

在 VPS 上部署 OpenClaw。抓取 104 職缺資料並了解資料結構。

**本週核心觀念**

- Data ingestion
- Web scraping pipeline
- Raw data vs processed data

------------------------------------------------------------------------

## Week 6 --- 儲存職缺資料

**本週任務**

建立 job table，將 crawler 抓到的資料寫入資料庫。

**本週核心觀念**

- 資料庫 schema
- 資料完整性
- Primary key

------------------------------------------------------------------------

## Week 7 --- 資料清洗

**本週任務**

處理薪資資料格式（面議、30k-40k 等）。寫 salary parser。

**本週核心觀念**

- Data cleaning
- Data normalization
- ETL transform

------------------------------------------------------------------------

## Week 8 --- 防止重複資料

**本週任務**

建立 hash 防重機制，避免相同職缺重複存入資料庫。

**本週核心觀念**

- Idempotent pipeline
- Deduplication
- Data consistency

------------------------------------------------------------------------

# Month 3 --- Data Warehouse

## Week 9 --- PostgreSQL 與 Docker

**本週任務**

使用 Docker 建立 PostgreSQL container，將 SQLite 資料遷移到 Postgres。

**本週核心觀念**

- OLTP vs OLAP
- Database containerization
- Production database

------------------------------------------------------------------------

## Week 10 --- 資料建模

**本週任務**

建立 star schema：`job_fact`、`company_dim`、`skill_dim`。

**本週核心觀念**

- Data warehouse
- Dimension table
- Fact table
- Star schema

------------------------------------------------------------------------

## Week 11 --- SQL 分析

**本週任務**

撰寫 SQL 分析：熱門技能、平均薪資、城市需求。

**本週核心觀念**

- Aggregation
- Group by
- Analytical query

------------------------------------------------------------------------

## Week 12 --- 建立分析 API

**本週任務**

建立簡單 API（FastAPI）提供分析資料。

**本週核心觀念**

- Data service layer
- API for analytics
- Backend for dashboard

------------------------------------------------------------------------

# Month 4 --- Docker 與系統部署

## Week 13 --- Containerize crawler

**本週任務**

將 crawler 打包成 Docker image。

**本週核心觀念**

- Containerization
- Reproducible environment

------------------------------------------------------------------------

## Week 14 --- docker-compose

**本週任務**

使用 `docker-compose` 啟動 crawler 與 postgres。

**本週核心觀念**

- Multi-container architecture
- Service orchestration

------------------------------------------------------------------------

## Week 15 --- Containerize bot

**本週任務**

將 Telegram bot 加入 `docker-compose`。

**本週核心觀念**

- Microservice architecture
- Environment configuration

------------------------------------------------------------------------

## Week 16 --- 一鍵部署

**本週任務**

完成整個 pipeline 的一鍵啟動：`docker compose up`

**本週核心觀念**

- Infrastructure automation
- Deployment workflow

------------------------------------------------------------------------

# Month 5 --- Pipeline Automation

## Week 17 --- dbt

**本週任務**

建立 dbt models 進行資料轉換。

**本週核心觀念**

- Modern data stack
- Data lineage
- Transformation layer

------------------------------------------------------------------------

## Week 18 --- dbt test

**本週任務**

建立資料品質檢查（salary >= 0、title not null）。

**本週核心觀念**

- Data quality
- Data validation

------------------------------------------------------------------------

## Week 19 --- 排程系統

**本週任務**

使用 cron 排程 crawler、transform、analysis。

**本週核心觀念**

- Scheduling
- Batch pipeline

------------------------------------------------------------------------

## Week 20 --- 錯誤監控

**本週任務**

當 pipeline 失敗時透過 Telegram 發送通知。

**本週核心觀念**

- Monitoring
- Alerting
- Reliability

------------------------------------------------------------------------

# Month 6 --- Portfolio

## Week 21 --- GitHub 文件

**本週任務**

整理 GitHub repo 並撰寫 `README.md`。

**本週核心觀念**

- Technical documentation
- Open source project structure

------------------------------------------------------------------------

## Week 22 --- 系統架構圖

**本週任務**

繪製 ETL pipeline architecture diagram。

**本週核心觀念**

- System design
- Data architecture

------------------------------------------------------------------------

## Week 23 --- Dashboard

**本週任務**

建立 React / Next.js dashboard：技術需求排行榜、薪資分布、職缺趨勢。

**本週核心觀念**

- Data visualization
- Product thinking

------------------------------------------------------------------------

## Week 24 --- 模擬面試

**本週任務**

使用 AI 進行 Data Engineer 模擬面試並優化履歷。

**本週核心觀念**

- 系統設計回答
- 技術溝通能力
