# 🗂️ zhangcursor-hub — 论文笔记总厂库

**全部论文笔记的统一索引**：收录 arXiv 与四大顶会（ACL / EMNLP / NAACL / CVPR）论文的完整解析产物，一份索引查遍所有论文仓库。

<!-- 胶囊徽章带 -->
![Papers](https://img.shields.io/badge/Papers-1094-brightgreen?style=flat-square)
![Repos](https://img.shields.io/badge/Repos-9-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/ZhangCurosr/zhangcursor-hub?style=flat-square)
![Pipeline](https://img.shields.io/github/actions/workflow/status/ZhangCurosr/paper-notes/mineru_batch.yml?label=daily%20pipeline&style=flat-square)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)

## 这是什么

- **统一索引**：全部论文产物仓库的 URL → 仓库/路径 映射，一份 JSON 查遍所有论文
- **全自动**：每天 02:00 / 14:00 UTC 由云端流水线抓取新论文并更新本库
- **去重保障**：每篇论文只保留一套完整产物（`paper.pdf` + `full.md` + `images/` + `meta.json`），冗余目录定期自动清理

## 统计

- 论文总数：**1094**

- **arXiv**：341 篇
- **ACL 2024**：167 篇
- **NAACL 2024**：156 篇
- **CVPR 2023**：154 篇
- **EMNLP 2024**：152 篇
- **CVPR 2024**：124 篇

## 产物仓库

| 仓库 | 论文数 |
|---|---|
| [`ZhangCurosr/zhangcursor-papers-acl-2024-001`](https://github.com/ZhangCurosr/zhangcursor-papers-acl-2024-001) | 167 |
| [`ZhangCurosr/zhangcursor-papers-arxiv-ai-001`](https://github.com/ZhangCurosr/zhangcursor-papers-arxiv-ai-001) | 99 |
| [`ZhangCurosr/zhangcursor-papers-arxiv-cl-001`](https://github.com/ZhangCurosr/zhangcursor-papers-arxiv-cl-001) | 61 |
| [`ZhangCurosr/zhangcursor-papers-arxiv-cv-001`](https://github.com/ZhangCurosr/zhangcursor-papers-arxiv-cv-001) | 73 |
| [`ZhangCurosr/zhangcursor-papers-arxiv-lg-001`](https://github.com/ZhangCurosr/zhangcursor-papers-arxiv-lg-001) | 108 |
| [`ZhangCurosr/zhangcursor-papers-cvpr-2023-001`](https://github.com/ZhangCurosr/zhangcursor-papers-cvpr-2023-001) | 154 |
| [`ZhangCurosr/zhangcursor-papers-cvpr-2024-001`](https://github.com/ZhangCurosr/zhangcursor-papers-cvpr-2024-001) | 124 |
| [`ZhangCurosr/zhangcursor-papers-emnlp-2024-001`](https://github.com/ZhangCurosr/zhangcursor-papers-emnlp-2024-001) | 152 |
| [`ZhangCurosr/zhangcursor-papers-naacl-2024-001`](https://github.com/ZhangCurosr/zhangcursor-papers-naacl-2024-001) | 156 |

## 索引格式（index.json）

```json
{
  "source": "https://arxiv.org/pdf/2608.11528v1.pdf",
  "repo": "ZhangCurosr/zhangcursor-papers-arxiv-cl-001",
  "path": "2026-08-13/Group-Alignment-..._97c188ed",
  "title": "Group-Alignment-Induced-Sycophancy: ...",
  "venue": "arXiv",
  "date": "2026-08-13"
}
```

## 怎么用

```python
# 按来源 / 标题 / venue 检索（任意语言，读 index.json 即可）
import json, urllib.request
idx = json.load(urllib.request.urlopen(
    "https://raw.githubusercontent.com/ZhangCurosr/zhangcursor-hub/main/index.json"))
hits = [r for r in idx if "sycophancy" in r["title"].lower()]
for h in hits:
    print(h["repo"], h["path"])   # → 去对应仓库取 paper.pdf / full.md / images/
```

## 更新机制

- 每日流水线（`paper-notes` 仓库 Actions）自动追加新论文
- “Dedup Repos” workflow 一键去重并重建本索引（覆盖式，保证索引与仓库实际一致）

## Limits

- 索引仅收录**完整产物**（有 PDF 且已解析）的论文
- 论文全文请到对应产物仓库取用，本库不存原文
- 各仓库容量上限 500MB，超限自动开新仓（`-002`），索引会跟随归一

## License

MIT
