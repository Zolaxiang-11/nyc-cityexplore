# 纽约宜居方程 · 长文主站（静态站点）

本文件夹为**可独立部署**的完整静态站点：首页 `index.html` + 四章叙事内嵌的所有可视化 iframe 及其数据依赖。

## 目录结构（模块化）

| 路径 | 说明 |
|------|------|
| `index.html` / `main.js` / `styles.css` | 主站入口与样式 |
| `data/` | `site-content.json`（文案与 iframe 路径）、`integration-manifest.json`、终章占位数据等 |
| `output/` | 第四篇章「微观生态」汇总数据（环境 iframe 从 `apps/07-environment/` 经 `../../output/` 读取） |
| `apps/` | 按叙事顺序编号的嵌入子应用（人口→经济→交通→环境） |

### `apps/` 子目录一览

| 目录 | 篇章 | 原项目名（便于对照） |
|------|------|----------------------|
| `01-population-yearly` | 社会底色 | 人口年度变化 |
| `02-population-rings` | 社会底色 | 人口圈层图 |
| `03-education-level` | 社会底色 | 教育水平 |
| `04-safety-linebox` | 社会底色 | 公共安全 |
| `05-economy` | 经济账本 | nyc-pulse |
| `06-transport` | 时空脉搏 | Visualization-Work3 |
| `07-environment` | 微观生态 | nyc-urban-environment |

## 本地预览

在项目根目录（本 README 所在目录）启动任意静态文件服务，例如：

```bash
# Python 3
python -m http.server 8080
```

浏览器访问：`http://localhost:8080/`。

> 必须通过 HTTP(S) 访问（不要直接用 `file://` 打开），否则 `fetch` 加载 JSON 会失败。

## 部署到 GitHub Pages

1. 将**本文件夹整个内容**作为仓库根目录推送（或推送到 `docs/` 并在仓库 Settings → Pages 中选择对应分支与目录）。
2. 站点内资源均为**相对路径**，无需改配置即可在子路径发布；若使用自定义域名，仅需在 Pages 设置里绑定域名。

## 更新站点内容

修改叙事或 iframe 列表：编辑 `data/site-content.json`。  
各子应用入口与数据路径索引：见 `data/integration-manifest.json`。  
更新某一嵌入图表：替换对应 `apps/xx-*/` 下的文件（更新 HTML 里 assets 的 `?v=` 缓存参数时可顺手递增）。

## 从上游工程重新打包（可选）

若你在本仓库**上一级**仍保留完整的 `longform-main-site` 开发目录，可在上级目录执行 `_copy-longform-deploy.ps1`（与本文件夹同级脚本）重新同步生成 `nyc-longform-github`。

---

数据来源于课程子项目整合；主站仅负责叙事与排版。
