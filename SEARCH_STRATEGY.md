# PubMed 检索策略 — FGFR × 肿瘤 每日文献速递

> 最后更新: 2026-07-12

## 检索式结构

```
((FGFR基因) OR (FGFR抑制剂)) AND (肿瘤)
```

## 完整检索式

```
(
  (
    "Receptors, Fibroblast Growth Factor"[Mesh]
    OR FGFR1[tiab] OR FGFR2[tiab] OR FGFR3[tiab] OR FGFR4[tiab]
    OR FGFRL1[tiab] OR FGFR[tiab]
    OR "fibroblast growth factor receptor"[tiab]
  )
  OR
  (
    "FGFR inhibitor"[tiab] OR "FGFR inhibitors"[tiab]
    OR "fibroblast growth factor receptor inhibitor"[tiab]
    OR "fibroblast growth factor receptor inhibitors"[tiab]
    OR erdafitinib[tiab] OR pemigatinib[tiab]
    OR futibatinib[tiab] OR infigratinib[tiab]
    OR Balversa[tiab] OR Pemazyre[tiab] OR Lytgobi[tiab] OR Truseltiq[tiab]
    OR tinengotinib[tiab] OR "TT-00420"[tiab]
    OR "debio 1347"[tiab] OR "debio-1347"[tiab] OR zoligratinib[tiab]
    OR rogaratinib[tiab] OR "BAY 1163877"[tiab]
    OR AZD4547[tiab] OR LY2874455[tiab] OR E7090[tiab] OR ASP5878[tiab]
    OR derazantinib[tiab] OR "ARQ 087"[tiab] OR "ARQ-087"[tiab]
    OR PRN1371[tiab] OR "HMPL-453"[tiab]
    OR fisogatinib[tiab] OR "BLU-554"[tiab] OR FGF401[tiab]
    OR "H3B-6527"[tiab]
  )
)
AND
(
  "Neoplasms"[Mesh]
  OR cancer[tiab] OR cancers[tiab] OR cancerous[tiab]
  OR tumor[tiab] OR tumors[tiab] OR tumour[tiab] OR tumours[tiab]
  OR neoplasm[tiab] OR neoplasms[tiab] OR neoplastic[tiab]
  OR carcinoma[tiab] OR carcinomas[tiab] OR carcinomatous[tiab]
  OR sarcoma[tiab] OR sarcomas[tiab]
  OR adenocarcinoma[tiab] OR adenocarcinomas[tiab]
  OR malignan*[tiab]
  OR lymphoma[tiab] OR lymphomas[tiab]
  OR leukemia[tiab] OR leukaemia[tiab]
  OR melanoma[tiab] OR melanomas[tiab]
  OR oncolog*[tiab]
)
```

## 检索参数

| 参数 | 值 | 说明 |
|------|-----|------|
| 数据源 | PubMed (NCBI E-utilities) | 免费 API，无需 Key |
| 日期字段 | `[Date - Entrez]` | 论文被 PubMed 收录的日期 |
| 检索范围 | `reldate=1` + `datetype=edat` | 前 1 天内收录的文献 |
| 字段标签 | `[Mesh]` = MeSH 主题词，`[tiab]` = Title/Abstract | 精确限定检索区域 |
| 最大返回 | 100 篇 | 超过自动截断 |

## 各组说明

### 第一组：FGFR 基因（8 个检索词）
- `"Receptors, Fibroblast Growth Factor"[Mesh]` — MeSH 主题词，自动包含所有下位词
- 各基因名 `[tiab]` — 在标题和摘要中精确匹配
- `FGFR[tiab]` — 捕获未指定亚型的泛 FGFR 提及
- `"fibroblast growth factor receptor"[tiab]` — 全称匹配

### 第二组：FGFR 抑制剂（36 个检索词）
- 通称（4 个）：FGFR inhibitor(s), fibroblast growth factor receptor inhibitor(s)
- 已上市药（8 个）：erdafitinib/pemigatinib/futibatinib/infigratinib + 商品名 Balversa/Pemazyre/Lytgobi/Truseltiq
- 在研药物（24 个）：tinengotinib/TT-00420/debio 1347/zoligratinib/rogaratinib/BAY 1163877/AZD4547/LY2874455/E7090/ASP5878/derazantinib/ARQ 087/PRN1371/HMPL-453/fisogatinib/BLU-554/FGF401/H3B-6527

### 第三组：肿瘤（27 个检索词）
- `"Neoplasms"[Mesh]` — MeSH 主题词，覆盖所有肿瘤类型
- 各癌种中英文变体 `[tiab]`：cancer/tumor/carcinoma/sarcoma/adenocarcinoma/malignan*/lymphoma/leukemia/melanoma/oncolog*

## Python 实现

脚本文件：`daily_pubmed_search.py`

关键函数：
- `build_search_query()` — 组装检索式（行 225）
- `pubmed_search()` — 执行 ESearch 并返回 PMID 列表（行 97）
- `pubmed_fetch()` — 通过 EFetch 获取文献详情（行 115）
