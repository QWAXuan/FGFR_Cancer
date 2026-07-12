# FGFR_Cancer

> FGFR 基因 × FGFR 抑制剂 × 肿瘤 — 每日 PubMed 文献自动速递

本仓库由 ZCode 自动化流水线每日维护,自动检索前一天进入 PubMed 索引的相关论文,经 AI 阅读摘要并总结主要发现后,生成按日期命名的 Markdown 报告。

## 检索范围

- **靶点**:FGFR1 / FGFR2 / FGFR3 / FGFR4 / FGFRL1
- **干预**:FGFR 抑制剂(16 种:erdafitinib、pemigatinib、futibatinib、infigratinib、tinengotinib、debio 1347、rogaratinib、AZD4547 等)
- **疾病**:肿瘤 / 癌症(MeSH `Neoplasms` 自动展开 + 文本词)
- **日期口径**:`[Date - Entrez]`(论文进入 PubMed 索引的日期)
- **数据来源**:PubMed / MEDLINE(NCBI E-utilities)

## 报告命名

`YYYY-MM-DD.md` — 每日一篇,含每篇论文的题目、作者、期刊、DOI、摘要及 AI 总结的主要发现。
