# HORROR LAB｜LLM Wiki

## 專案簡介

HORROR LAB｜LLM Wiki 是一個以恐怖文化、恐怖敘事與作品研究為核心的可持續維護知識專案。專案將在查證、引用與著作權規則下，逐步建立適合讀者閱讀、也適合 AI 協作維護的 Wiki 結構。

## 預定成果

- 建立六大知識主題的可追溯 Wiki。
- 建立來源、引用、衝突處理與內容維護流程。
- 在後續獲准階段製作以 Wiki 為基礎的 HTML 簡報。
- 在後續獲准階段設計可解釋的 Graph / Loop 關聯與工作流程。

## 目前進度

### 第一階段：專案基礎架構

已建立：

- `AGENTS.md`：AI 工作規則與階段限制。
- `README.md`：專案說明與進度。
- `.gitignore`：暫存檔、機密資料與建置產物排除規則。
- `raw/`、`wiki/`、`workflow/`、`slides/`、`reports/`：後續階段使用的空目錄。

### 第二階段：候選資料與受控來源整理

已完成：

- `reports/candidate-sources.md`：候選學術資料清單。
- `raw/papers/`：三篇使用者提供的 PDF 原始檔案。
- `workflow/source-register.md`：來源、版本、授權、頁數與 SHA-256 登錄。
- `workflow/ingest-manifest.json`：受控 ingest 對應表。
- `wiki/`：三篇依摘要與書目建立的草稿條目。
- `workflow/graph.json`：具證據邊界的關係草稿。
- `workflow/loop-checklist.md`：來源與條目重複檢查流程。
- `slides/horror-lab-research.html`：以已查證內容製作的研究來源導覽草稿。

目前限制：三篇 Wiki 條目仍待逐段全文複核；尚未建立完整自動化 Graph / Loop 執行程式、部署網站或建立正式發布版本。所有新增檔案目前尚未 commit 或 push。

詳細工作規則請先閱讀 [`AGENTS.md`](./AGENTS.md)。
