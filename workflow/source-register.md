# HORROR LAB｜來源登錄表

## 登錄狀態

- 工作階段：來源登錄／ingest 前整理
- 登錄日期：2026-11-19
- 原始資料位置：`raw/papers/`
- 狀態：已完成本次作業所需來源登錄與受控 ingest
- 本表不是 Wiki 知識條目，也不替代逐段閱讀、引用定位或衝突查證。
- 原始 PDF 保持不修改；本階段只登錄書目、來源、檔案完整性與預定主題。

## 來源清單

### P-000

- 原始檔案：`raw/papers/000.pdf`
- 題名：Do film soundtracks contain nonlinear analogues to influence emotion?
- 作者：Daniel T. Blumstein；Richard Davitian；Peter D. Kaye
- 出版資訊：Biology Letters, 6(6), 751–754, 2010
- DOI：https://doi.org/10.1098/rsbl.2010.0333
- 來源／查證頁面：https://researchinnovation.kingston.ac.uk/en/publications/do-film-soundtracks-contain-nonlinear-analogues-to-influence-emot-2/
- 預定主要主題：影像、聲音與感官設計
- 候選交叉主題：恐怖心理；作品、創作者與影響
- 授權／存取：來源頁面列有 DOI 與可取得文件入口；正式採用前仍需確認所用版本與授權條件。
- PDF 格式：PDF header `%PDF-`，EOF marker detected
- 頁數：4
- 檔案大小：132,073 bytes
- SHA-256：`ed232791490a744fe887c6ac6b80df49c93b6f5db19a68c52878e1eb25ba4280`
- 去重狀態：目前以 DOI 作為識別鍵；尚未與其他檔案做全文去重。
- 摘要／條目狀態：已建立對應 Wiki 條目，完成教學整理與限制說明。

### P-001

- 原始檔案：`raw/papers/001.pdf`
- 題名：Surfing uncertainty with screams: Predictive processing, error dynamics and horror films
- 作者：Mark Miller；Ben White；Coltan Scrivner
- 出版資訊：Philosophical Transactions of the Royal Society B: Biological Sciences, 379(1895), Article 20220425, 2024
- DOI：https://doi.org/10.1098/rstb.2022.0425
- 來源／查證頁面：https://pure.au.dk/portal/en/publications/surfing-uncertainty-with-screams-predictive-processing-error-dyna/
- 預定主要主題：恐怖心理
- 候選交叉主題：敘事與文本技術；影像、聲音與感官設計
- 授權／存取：研究機構頁面標示 final published version 與 CC BY；正式採用前仍需核對本地檔案是否為該版本。
- PDF 格式：PDF header `%PDF-`，EOF marker detected
- 頁數：11
- 檔案大小：534,699 bytes
- SHA-256：`e75f8a309e34980a1332093e2d0238c84abf9ff3b8b5781ad26ce23e203f9ab1`
- 去重狀態：目前以 DOI 作為識別鍵；尚未與其他檔案做全文去重。
- 摘要／條目狀態：已建立對應 Wiki 條目，完成教學整理與限制說明。

### P-002

- 原始檔案：`raw/papers/002.pdf`
- 題名：The role of excitement and enjoyment through subjective evaluation of horror film scenes
- 作者：Botond László Kiss；Anita Deák；Martina Dominika Veszprémi；Albert Blénessy；András N. Zsidó
- 出版資訊：Scientific Reports, 14(1), Article 2987, 2024
- DOI：https://doi.org/10.1038/s41598-024-53533-y
- 來源／查證頁面：https://crossmark.crossref.org/dialog/?doi=10.1038%2Fs41598-024-53533-y
- 預定主要主題：恐怖心理
- 候選交叉主題：影像、聲音與感官設計；作品、創作者與影響
- 授權／存取：PDF 內嵌資訊列有 Creative Commons BY 4.0 連結；正式採用前仍需以出版者頁面確認版本與授權適用範圍。
- PDF 格式：PDF header `%PDF-`，EOF marker detected
- 頁數：8
- 檔案大小：949,324 bytes
- SHA-256：`223d24697fcff937616c8d36094273241b0f46e704003b5b94e00c7312324a5c`
- 去重狀態：目前以 DOI 作為識別鍵；尚未與其他檔案做全文去重。
- 摘要／條目狀態：已建立對應 Wiki 條目，完成教學整理與限制說明。

## 後續 ingest 前必做事項

1. 使用者確認三筆來源與主要主題歸類。
2. 核對每個 PDF 的版本、授權與可引用頁碼。
3. 逐篇閱讀並建立來源摘要、主張清單與引用定位。
4. 與候選清單及其他來源比對，記錄重複與文獻衝突。
5. 取得明確授權後才可執行 ingest；正式 Wiki 條目另依 `AGENTS.md` 規範建立。
