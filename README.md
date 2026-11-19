# HORROR LAB｜LLM Wiki

本專案以「恐怖心理與恐怖敘事中的觀眾反應」為主題，將可追溯來源整理成 Wiki 草稿，並用 Wiki 產生入門教學型 HTML 簡報。

## 目前成果

- 5 篇 PDF 已登錄並通過標頭、頁數與 SHA-256 檢查。
- 5 篇來源各自對應 1 篇 Wiki 草稿，詳見 [`workflow/ingest-manifest.json`](./workflow/ingest-manifest.json)。
- [`slides/horror-lab-research.html`](./slides/horror-lab-research.html) 為可直接瀏覽的教學簡報。
- [`workflow/graph.json`](./workflow/graph.json) 與 [`workflow/loop-checklist.md`](./workflow/loop-checklist.md) 說明資料取得、驗證、整理與生成流程。
- [`reports/submission-notes.md`](./reports/submission-notes.md) 可作為課程作業提交說明。

## 目錄

- `raw/papers/`：原始 PDF；只保留來源檔，不在此直接改寫。
- `wiki/`：帶有來源、證據與限制段落的 Wiki 草稿。
- `workflow/`：來源登錄、ingest manifest、Graph 與 Loop 檢查。
- `slides/`：教學型 HTML 簡報。
- `reports/`：候選來源與提交驗收說明。

完整工作規則請先閱讀 [`AGENTS.md`](./AGENTS.md)。
