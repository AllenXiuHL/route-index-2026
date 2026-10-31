# 技术路线索引 · 2026

面向**自动驾驶规控工程师 / 具身智能算法工程师 / Agent 系统开发者**的静态路线索引页。
单文件、零外部依赖（无 CDN、无外部字体、无第三方脚本），断网也能完整打开。

一句话：不是"条目清单"，而是给每个方向配了**路线图 → 方案对比 → 关键条目 → 洞察 → 论文路径**五层。

> **线上**：<https://allenxiuhl.github.io/route-index-2026/>
> **仓库**：<https://github.com/AllenXiuHL/route-index-2026>

## 内容规模

| 项 | 数量 |
| --- | --- |
| 方向 | 3（自动驾驶 / 具身 / Agent） |
| 子线 | 12（每方向 4 条） |
| 条目 | 38（开源 / 论文 / 框架 / 事件） |
| 论文与仓库 | 41（arXiv 46 个直达链接，逐条用 arXiv API 核过标题与编号） |
| 洞察 | 每方向 3 条 + 跨方向 3 条 |
| 读者路径 | 3 类角色的「先看 / 押注 / 别踩」 |

## 每个方向的结构

1. **核心叙事**——40 字内说清当前矛盾
2. **关键数字条**——4 个可对照的量化锚点
3. **技术路线图**——四段式演进，标代表方案与当期约束
4. **方案对比表**——同一道题的不同答法，最后一列永远写「代价」
5. **子线条目**——12 条/方向，带类型徽章与数字加粗
6. **洞察**——带算式的分析（时延换成米、数据缺口的年数、500 题的置信区间）
7. **论文与开源路径**——按主题分组，链接直达 arXiv / GitHub
8. **关键分歧**——深色块收尾

## 预览

```powershell
Start-Process "index.html"
# 或
python -m http.server 8099
```

## 文件

```text
route-index/
├── index.html              # 交付文件：结构 + 样式 + 交互全部内联
├── dist/index.html         # 部署副本（与根目录一致）
├── route-index-static.zip  # 可直接拖拽上传的部署包
├── build_site.py           # 生成器：内容与数据都在这里，改完重跑即可
└── README.md
```

## 改内容

内容集中在 `build_site.py` 顶部的数据区：

```python
AD = { "narrative": "...", "keynums": [...], "route": [...],
       "compare": {...}, "sublines": [...], "insights": [...],
       "papers": [...], "divergence": "..." }
```

改完执行：

```powershell
python build_site.py
```

会重新生成 `index.html`（并打印条目/论文计数）。改完记得把 `index.html` 复制到 `dist/` 再打包。

## 上线

- **拖拽**：把 `route-index-static.zip` 拖进 <https://app.netlify.com/drop> 或 <https://vercel.com/new>。
- **Vercel CLI**：`npx vercel deploy --prod --yes --token $VERCEL_TOKEN`
- **Netlify CLI**：`npx netlify deploy --prod --dir . --site $NETLIFY_SITE_ID --auth $NETLIFY_AUTH_TOKEN`
- **GitHub Pages**：推到仓库后在 Settings → Pages 选 `main / root`。
- **自有服务器**：只有一个 `dist/index.html`，拷进任意静态目录即可。

## 说明

- 内容截至 2026 年 10 月；数字与项目名以公开信息为准。
- 论文链接均指向 arXiv 原文或官方仓库，已逐条核验；没有公开一手来源的条目标 “—”，不硬凑链接。
- 本页为路线观察，不构成投资或选型建议。
